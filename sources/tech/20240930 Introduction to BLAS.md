[#]: subject: "Introduction to BLAS"
[#]: via: "https://fedoramagazine.org/introduction-to-blas/"
[#]: author: "Roman Gherta https://fedoramagazine.org/author/romangherta/"
[#]: collector: "lujun9972/lctt-scripts-1705972010"
[#]: translator: " "
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

Introduction to BLAS
======

![][1]

Photo by [Zhifei Zhou][2] on [Unsplash][3] cropped

Basic Linear Algebra Subprograms or [BLAS][4] is a specification created in the 70s/80s by members of academia from US public institutions. The aim was the standardization and speed improvement for low-level linear algebra operations. This initially involved vector operations (Level 1). Over time, BLAS came to support more complex algorithms like vector-matrix operations (Level 2) and in the end matrix-matrix operations (Level 3).

For a general overview, the [Netlib Quick Reference Guide][5] is a good start. Be sure to check out the References section of the Quick Reference Guide for more detailed explanations and examples. It cites three research papers that were the basis of this specification. Jack Dongarra seems to be a key figure in this field. You can find those papers in the public domain.

Take a look at what the specification says about matrix operations. Specific operations involving symmetric, hermitian, and triangular matrices exist because these special cases can improve performance. We will focus on GEMM the general matrix-matrix operation:

```

    options         dim      scalar matrix  matrix  scalar matrix
    xGEMM ( TRANSA, TRANSB, M, N, K, ALPHA, A, LDA, B, LDB, BETA, C, LDC )

```

According to the guide:

  * xGEMM is the name of a function that performs a general x datatype matrix-matrix operation
  * This function solves the matrix-matrix operation
    * C <= alpha * op(A) * op(B) + beta * C where A,B,C rectangular matrices
  * TRANSA/TRANSB refer to the extra operation op(A) and op(B) and can be either N (No transpose) or T (Transpose) or C (Conjugate transpose)
  * M, N, K – are dimensions ie A has dimensions m x k, B is k x n and C is m x n
  * LDA and LDB are the leading dimensions of matrices A and B



The implemented function/procedure should have the above signature. This matrix-matrix operation is generic and by changing the options and the scalars, you can define a sum and/or a product operation. The specification is generic in this sense. For example, if we want to test a matrix product, we have to make _BETA=0_ and _TRANSA=TRANSB=N_.

The specification breaks down higher-level matrix operations into operations of lower level by partitioning the matrix into smaller components and calling lower-level BLAS functions. This allows the partitioned components to fit into smaller cache sizes (L3-L1) and improves computational speed.

### Netlib

The first implementations of this specification were written in Fortran – an important language for scientific and high-performance computing. Additional layers and libraries were developed, such as LAPACK, which relies on BLAS. LAPACK specializes in higher-level linear algebra operations like linear systems, factorization, eigenvalues, etc. You can still find all these libraries on the [Netlib][6] website.

Separation of concerns allowed BLAS to grow and specialize in matrix operations to take advantage of underlying hardware architectures. This also enabled LAPACK to specialize in mathematical-related domains. The [TOP500][7] HPC centers use a variation of these libraries for rating.

### OpenBLAS

GotoBLAS, developed by Kazushige Goto at TACC, is another implementation of the BLAS specification that became popular in the years 2000s. A notable feature of this library is the use of handwritten assembly code for improved performance. An open-source version became available to the public under a BSD license but is now discontinued.

[OpenBLAS][8] was forked from GotoBLAS2 by Zhang Xianyi in 2011 while at UT Austin. It is currently maintained and updated to take advantage of new processor architectures and capabilities. It has support for RISC-V in its latest versions.

Over the years OpenBLAS had some of the best benchmark scores close to Intel MKL. Intel MKL is another notable library from the 90s. Intel MKL became oneMKL in 2020 to align with the oneAPI specification. The specification defines a hardware-agnostic api that should work across emerging heterogeneous computing (CPU+accelerators). Note the libraries we are discussing here work exclusively on CPU.

### FlexiBLAS

[FlexiBLAS][9] was created by Martin Kohler and Jens Saak from MPI Magdeburg. In a 2013 paper, they mention a few problems related to the linear algebra ecosystem from lapack to plasma, magma, atlas, and the blas implementation used by each of these libraries. The mentioned issues are: linked libraries and their dependencies, profiling and debugging, and various incompatibilities. FlexiBLAS is another layer of indirection that manages all these problems and allows one to switch between different BLAS backends at runtime using an environment variable or configuration file. Spend some time reading the man page. It manages the problems by programmatically calling in its source code the POSIX functions dlopen/dlsym etc. For a list of available backends:

```

    user@fedora:~$ dnf install flexiblas
    user@fedora:~$ flexiblas list
    System-wide (config directory):
     NETLIB
       library = libflexiblas_netlib.so
     OPENBLAS-OPENMP
       library = libflexiblas_openblas-openmp.so

```

We will need the shared objects and the header files so we’ll install the development version as below.

```

    user@fedora:~$ dnf install flexiblas-devel gcc
    user@fedora:~$ rpm -ql flexiblas-devel
    /usr/include/flexiblas
    /usr/include/flexiblas/blas_gnu.h
    /usr/include/flexiblas/cblas.h
    /usr/include/flexiblas/lapack.h
    /usr/lib64/libflexiblas.so
    /usr/lib64/libflexiblas64.so
    ...

```

#### Examples

Let’s make a matrix multiplication program and compare the performance. Here we multiply 2 matrices using the well-known algorithm rows x columns. We will try to keep the program as small as possible so excuse the lack of programming conventions coming from a pascal/fortran user. We are using Fedora Workstation 40 with 6 CPU and 8 GB RAM.

```

    user@fedora:~$ cat <<EOF > simple_mm.c
    #include "stdio.h"
    #include "stdlib.h"
    #define N 5000

    double A[N][N], B[N][N], C[N][N];

    int main(){

        // seed with random values
        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++) {
              A[i][j]=rand(); B[i][j]=rand(); C[i][j]=0;
          }

        // matrix multiply
        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++)
            for(int p=0; p<N; p++) {
              C[i][j] = A[i][p] * B[p][j] + C[i][j];
            }
    }
    EOF

    user@fedora:~$ gcc simple_mm.c -o simple_mm.o
    user@fedora:~$ time ./simple_mm.o
    real    13m46.145s
    user    13m44.369s
    sys     0m0.493s

```

For 5000 rows/cols square matrix, the average time was 12 minutes on a single core. Since this laptop has more cores available, we can check how much better we can get with OpenMP.

```

    user@fedora:~$ cat <<EOF > omp_mm.c
    #include "stdio.h"
    #include "stdlib.h"
    #include "omp.h"
    #define N 5000

    double A[N][N], B[N][N], C[N][N];

    int main(){

        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++){
              A[i][j]=rand(); B[i][j]=rand(); C[i][j]=0;
          }

        #pragma omp parallel for shared(C)
        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++)
            for(int p=0; p<N; p++){
              C[i][j] = A[i][p] * B[p][j] + C[i][j];
            }
    }
    EOF

    user@fedora:~$ gcc omp_mm.c -o omp_mm.o -fopenmp
    user@fedora:~$ time OMP_NUM_THREADS=4 ./omp_mm.o
    real        3m14.798s
    user     12m46.950s
    sys     0m0.645s

```

So with 2 lines of OpenMP, we were able to get 3 minutes when running on 4 cores. Let’s try to use flexiblas now and see the difference. We will call the cblas interface from the flexiblas-devel package. We also need to link the library exactly as detailed in the [Fedora Docs][10].

```

    user@fedora:~$ cat <<EOF > cblas_mm.c
    #include "stdio.h"
    #include "stdlib.h"
    #include "flexiblas/cblas.h"
    #define N 5000

    double A[N][N], B[N][N], C[N][N];

    int main(){

        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++){
              A[i][j]=rand(); B[i][j]=rand(); C[i][j]=0;
          }

        cblas_dgemm(CblasRowMajor,CblasNoTrans,CblasNoTrans, N,N,N, 1, \
                    &A[0][0],N, &B[0][0],N, 0,&C[0][0],N);
    }
    EOF

    user@fedora:~$ gcc cblas_mm.c -o cblas_mm.o -lflexiblas
    user@fedora:~$ time ./cblas_mm.o
    real      0m1.690s
    user      0m5.820s
    sys       0m0.301s

```

Notice this time the program ran in 2 seconds. The extra argument CblasRowMajor indicates that C saves multidimensional arrays in memory by rows, as opposed to Fortran, for example.

#### Profiling

One other interesting feature that flexiblas provides is profiling and debugging. It is doing so using the concept of hooks. For this, we need to either create and build the shared object or install it. A sample profile hook is available as a separate Fedora Linux package.

```

    user@fedora:~$ dnf install -y flexiblas-hook-profile
    user@fedora:~$ rpm -ql flexiblas-hook-profile
    /usr/lib64/flexiblas/libflexiblas_hook_profile.so
    ...
    user@fedora:~$ flexiblas hook list
    Available hooks:
      PROFILE (/usr/lib64/flexiblas//libflexiblas_hook_profile.so)

```

Now that we have the hook available locally, let’s use it to profile a sample program by calling the Fortran interface. You can use the examples from FlexiBLAS github page to build your own profilers.

```

    user@fedora:~$ cat <<EOF > profile_mm.c
    #include "stdio.h"
    #include "stdlib.h"
    #define N 5000

    extern void dgemm_ (char* transa, char* transb, \
    int* m, int* n, int* k, \
    double* alpha, double* a, int* lda, double* b, int* ldb, \
    double* beta, double* c, int* ldc);

    double A[N][N], B[N][N], C[N][N];
    int dim=N; double alpha=1; double beta=0;

    int main(){

        for(int i=0; i<N; i++)
          for(int j=0; j<N; j++){
             A[i][j]= rand(); B[i][j]= rand(); C[i][j]= 0;
          }

        for(int i=0; i<5; i++)
         dgemm_("N","N", &dim,&dim,&dim, &alpha,&A[0][0],&dim, \
         &B[0][0],&dim, &beta,&C[0][0],&dim);
    }
    EOF

    user@fedora:~$ gcc profile_mm.c -o profile_mm.o -lflexiblas

    user@fedora:~$ FLEXIBLAS_HOOK=PROFILE ./profile_mm.o
    <flexiblas-profile> Write profile to flexiblas_profile.txt

    user@fedora:~$ grep dgemm flexiblas_profile.txt
      dgemm                                 5      4.97674

```

FlexiBLAS sees use by a diverse range of packages. These range from core libraries in R and Python to chemical simulations and linear algebra packages.

```

    user@fedora:~$ dnf repoquery --whatrequires flexiblas-netlib
    COPASI-0:4.42.284-6.fc40.x86_64
    CheMPS2-0:1.8.9-22.fc40.i686
    MUMPS-0:5.6.2-3.fc40.i686
    Macaulay2-0:1.22-6.fc40.x86_64
    R-core-0:4.3.3-1.fc40.i686
    gromacs-libs-0:2024-1.fc40.x86_64
    ocaml-lacaml-0:11.0.10-9.fc40.x86_64
    octave-6:8.4.0-6.fc40.i686
    python3-numpy-1:1.26.4-1.fc40.x86_64
    ...

```

### More matrices

One way to think about matrices is to consider each column as coordinates (x,y,z) in space. In this way a 3xn matrix can represent a 3d object. The more complex the object, and the more points it has, the wider the matrix will be. Let’s use this concept to represent a 3D cube:

```

    -1 -1 -1 -1  1  1  1  1
    -1 -1  1  1 -1 -1  1  1
    -1  1 -1  1 -1  1 -1  1

```

Another way to think about matrices is in terms of linear transformations. There are a few well-known [transformations][11] that we can apply to a vector space. We can translate, scale, or rotate. Each of these transformations is represented by a well-known matrix. Those shown here are for the following example.

```

    xROTATION                  SCALE              TRANSLATION
    1      0         0  0      sx  0   0   0      1   0   0  tx
    0  cos(t)  -sin(t)  0      0   sy  0   0      0   1   0  ty
    0  sin(t)   cos(t)  0      0   0   sz  0      0   0   1  tz
    0      0         0  1      0   0   0   1      0   0   0   1

```

To rotate the cube in 3D, we will have to multiply the rotation matrix and the cube matrix. The resulting 4×8 matrix becomes the new rotated cube. We can make a continuous loop then rotate the cube by 3 degrees for each iteration and then render its coordinates on screen. Since our terminal is two-dimensional, we could neglect altogether the third row of the cube matrix. This way we will have a 2×8 matrix – meaning 8 points on a 2D scene. So in other words we will have the 2D projection of our 3D cube, also called an _orthographic projection_. The 2D projection will be relative to the 2D frame of reference of our terminal so this solves our problem with rendering the cube, the only thing we must account for is that the terminal coordinate (0,0) begins at the top left corner. So, the algorithm will have the following steps:

  * Scale unit cube
  * Rotate around y axis for perspective
  * Rotate 3 degress each loop
  * Translate to center of terminal and draw



All of the above steps are matrix multiplications. For drawing on the terminal we will use the ncurses library. Due to the terminal row/column height ratio we had to scale the cube more on the y-axis as you can see in the below example. You will also notice the cube matrix has an extra row of ones, as we converted to _homogeneous coordinates_.

```

    user@fedora:~$ dnf install ncurses-devel

    user@fedora:~$ cat <<EOF > cube.c
    #include "stdio.h"
    #include "math.h"
    #include "ncurses.h"
    #include "flexiblas/cblas.h"
    #include "string.h"
    #include "unistd.h"

    double myCube[4][8] = { { -1,  1, -1, -1,  1,  1, -1, 1 },
                            { -1, -1,  1, -1,  1, -1,  1, 1 },
                            { -1, -1, -1,  1, -1,  1,  1, 1 },
                            {  1,  1,  1,  1,  1,  1,  1, 1 } };
    double mScale[4][4] = { {  5,  0,  0,  0 },
                            {  0,  10, 0,  0 },
                            {  0,  0,  5,  0 },
                            {  0,  0,  0,  1 } };
    double mTranslate[4][4] = { {  1,  0,  0,  10 },
                                {  0,  1,  0,  50 },
                                {  0,  0,  1,  0  },
                                {  0,  0,  0,  1  } };
    double mRotateY30[4][4] =  {{  cos(M_PI/6), 0,  sin(M_PI/6),  0 },
                                {            0, 1,            0,  0 },
                                { -sin(M_PI/6), 0,  cos(M_PI/6),  0 },
                                {            0, 0,            0,  1 } };
    double mRotateX3[4][4] =  { { 1, 0, 0, 0 },
                                { 0, cos(M_PI/60), -sin(M_PI/60), 0 },
                                { 0, sin(M_PI/60), cos(M_PI/60),  0 },
                                { 0, 0, 0, 1 } };
    double scaledCube[4][8], tempCube[4][8], cntrCube[4][8];

    int main(){

        // scale the unit cube and rotate
        cblas_dgemm(CblasRowMajor,CblasNoTrans,CblasNoTrans, 4,8,4, \
            1,&mScale[0][0],4, &myCube[0][0],8, 0,&scaledCube[0][0],8);
        cblas_dgemm(CblasRowMajor,CblasNoTrans,CblasNoTrans, 4,8,4, \
            1,&mRotateY30[0][0],4, &scaledCube[0][0],8, 0,&myCube[0][0],8);

        initscr();
        curs_set(0);

        while(true){
            clear();
            memcpy(tempCube, myCube, 4*8*sizeof(double));

            // rotate 5 degrees
            cblas_dgemm(CblasRowMajor,CblasNoTrans,CblasNoTrans, 4,8,4, \
               1,&mRotateX3[0][0],4, &tempCube[0][0],8, 0,&myCube[0][0],8);

            // translate to middle
            cblas_dgemm(CblasRowMajor,CblasNoTrans,CblasNoTrans, 4,8,4, \
               1,&mTranslate[0][0],4, &tempCube[0][0],8, 0,&cntrCube[0][0],8);
            // render
            for(int j=0; j<8; j++)
               mvaddch((int)cntrCube[0][j], (int)cntrCube[1][j],'x');

            refresh();
            usleep(25000); // 25ms
        }

        getch();
        curs_set(1);
        endwin();

    }
    EOF

    user@fedora:~$ gcc cube.c -o cube.o -lflexiblas -lncurses
    user@fedora:~$ ./cube.o

```

We were able to draw a rotating cube in the terminal with relatively few lines. If we want to make the cube more realistic, we will need to add more vertices to the matrix that describes the cube. As a result, we will end up with a matrix with 3 rows and numerous columns. These are the types of practical matrices that BLAS libraries are optimized for.

Computer graphics is just one small application of linear algebra. When dealing with big models of thousands of points, with 4k monitors and color graphics, even this library is limited. This points out the need for specialized hardware (GPU/FPGA) for accelerated computing. These devices are programmed using different terms and programming paradigms from the ones used here, but matrix multiplication is still a core operation.

### Conclusions

Matrix multiplication is a relatively simple concept but notoriously slow. One major theoretical improvement was the Strassen Algorithm in the 70’s. The need to abstract a system of linear equations into a matrix form left us with this row-by-columns rule. The rule therefore needs to take into account all the linear system coefficients or, as in the case of Strassen, a relationship among these coefficients. Faced with these limitations, computational linear algebra had to improve on brute force and this is how BLAS came into being. Thanks to the Fedora Project contributors who maintain the above-mentioned packages.

--------------------------------------------------------------------------------

via: https://fedoramagazine.org/introduction-to-blas/

作者：[Roman Gherta][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://fedoramagazine.org/author/romangherta/
[b]: https://github.com/lujun9972
[1]: https://fedoramagazine.org/wp-content/uploads/2024/09/Intro-to-BLAS-816x345.jpg
[2]: https://unsplash.com/@phoebezzf?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[3]: https://unsplash.com/photos/blue-and-white-abstract-painting-3_x3NdhIp6s?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash
[4]: https://en.wikipedia.org/wiki/Basic_Linear_Algebra_Subprograms
[5]: https://www.netlib.org/blas/blasqr.pdf
[6]: https://netlib.org/
[7]: https://www.top500.org/project/linpack/
[8]: https://github.com/OpenMathLib/OpenBLAS
[9]: https://github.com/mpimd-csc/flexiblas
[10]: https://docs.fedoraproject.org/en-US/packaging-guidelines/BLAS_LAPACK/
[11]: https://open.gl/transformations
