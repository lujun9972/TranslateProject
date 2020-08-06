[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Federated learning improves how AI data is managed, thwarts data leakage)
[#]: via: (https://www.networkworld.com/article/3569528/federated-learning-improves-how-ai-data-is-managed-thwarts-data-leakage.html)
[#]: author: (Patrick Nelson https://www.networkworld.com/author/Patrick-Nelson/)

Federated learning improves how AI data is managed, thwarts data leakage
======
Researchers from Penn Medicine are studying new AI models using federated learning to improve how brain tumors are detected and treated.
Metamorworks / Getty Images

Privacy is one of the big holdups to a world of ubiquitous, seamless data-sharing for artificial intelligence-driven learning. In an ideal world, massive quantities of data, such as medical imaging scans, could be shared openly across the globe so that machine learning algorithms can gain experience from a broad range of data sets. The more data shared, the better the outcomes.

That generally doesn't happen now, including in the medical world, where privacy is paramount. For the most part, medical image scans, such as brain MRIs, stay at the institution level for analysis. The result is then shared, but not the original patient scan data.

**READ MORE:** [Cisco challenge winners use AI, IoT to tackle global problems][1]

Researchers believe a shift in the way data is managed could allow more information to reach learning algorithms outside of a single institution, which could benefit the entire system. Penn Medicine researchers propose using a technique called federated learning that would allow users to train an algorithm across multiple decentralized data sources without having to actually exchange the data sets.

Federated learning works by training an algorithm across many decentralized edge devices, as opposed running an analysis on data uploaded to one server.

"The more data the computational model sees, the better it learns the problem, and the better it can address the question that it was designed to answer," said Spyridon Bakas, an instructor in the Perelman School of Medicine at the University of Pennsylvania, in a [press release][2]. Bakas is lead author of a study on the use of federated learning in medicine that was [published in the journal _Scientific Reports_][3]. "Traditionally, machine learning has used data from a single institution, and then it became apparent that those models do not perform or generalize well on data from other institutions," Bakas said.

The Penn Medicine study focuses on the use of federated learning to design an AI system that will help clinicians better identify and treat brain tumors by sharing brain MRIs.

The problem right now, according to the researchers, is that all that useful sample data is held privately by the institution that collected it. It is analyzed locally by that institution, where a model is created. Each model can be then worked on by other institutions, but it's not ideal, because the local scenarios are all different.

A better way to do it, using federated AI, is to create a model—a brain tumor detecting model, for example—then share that model with hospitals globally. Instead of sharing data among institutions, the training model is distributed to the different data owners.

"A model trained at Penn Medicine, for example, can be distributed to hospitals around the world. Doctors can then train on top of this shared model, by inputting their own patient brain scans. Their new model will then be transferred to a centralized server. The models will eventually be reconciled into a consensus model that has gained knowledge from each of the hospitals, and is therefore clinically useful," the group explains.

Conceivably, hospitals around the world could participate if patient data is protected, privacy concerns are allayed, and lawmakers agree to it. The Penn Medicine group is in the middle of a large-scale test across institutions.

Researchers believe federated learning, also known as collaborative learning, will be the next wave of AI. (Google reportedly implemented one of the first use cases of federated learning to [improve predictive keyboards][4].)

Federated learning could create more opportunities to use AI in healthcare, according to Rivka Colen, co-author of the Penn Medicine study and an associate professor of radiology at the University of Pittsburgh School of Medicine. "I think it's a huge game changer," Colen said in the press release. "AI will revolutionize this field, because, right now, as a radiologist, most of what we do is descriptive. With deep learning, we're able to extract information that is hidden in this layer of digitized images."

The ides of sharing a common model, rather than individual data, could lend itself to other applications, such as IoT. Cornell University, for example, proposed a federated learning IoT framework for a cloud-edge architecture in a [paper][5] it published recently.

Join the Network World communities on [Facebook][6] and [LinkedIn][7] to comment on topics that are top of mind.

--------------------------------------------------------------------------------

via: https://www.networkworld.com/article/3569528/federated-learning-improves-how-ai-data-is-managed-thwarts-data-leakage.html

作者：[Patrick Nelson][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.networkworld.com/author/Patrick-Nelson/
[b]: https://github.com/lujun9972
[1]: https://www.networkworld.com/article/3569142/cisco-challenge-winners-use-ai-iot-to-tackle-global-problems.html
[2]: https://www.pennmedicine.org/news/news-releases/2020/july/new-machine-learning-method-allows-hospitals-to-share-patient-data-privately
[3]: https://www.nature.com/articles/s41598-020-69250-1
[4]: https://ai.googleblog.com/2017/04/federated-learning-collaborative.html
[5]: https://arxiv.org/abs/2002.10671
[6]: https://www.facebook.com/NetworkWorld/
[7]: https://www.linkedin.com/company/network-world
