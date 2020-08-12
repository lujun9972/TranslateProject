[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (9 reasons I upgraded from AngularJS to Angular)
[#]: via: (https://opensource.com/article/20/8/upgrade-angular)
[#]: author: (Alex Vasylenko https://opensource.com/users/avacodes)

9 reasons I upgraded from AngularJS to Angular
======
Angular's advantages and features make it worth the difficulty of
migrating from AngularJS.
![Blocks for building][1]

In 2010, Google released [AngularJS][2], an open source, JavaScript-based frontend structure for developing single-page applications (SPAs) for the internet. With its move to version 2.0 in 2016, the framework's name was shortened to [Angular][3]. AngularJS is still being developed and used, but Angular's advantages mean it's a smart idea to migrate to the newer version.

### AngularJS vs. Angular

AngularJS refers to all the 1.x versions of the framework. It transforms fixed HTML to dynamic HTML. Angular is an upgrade to AngularJS that is faster, offers a modular layout, leverages a command-line interface, and makes it easier to produce dynamic SPAs, among other advantages.

According to [StackOverflow's 2020 Developer Survey][4], more than 41% of developers use a version of Angular or AngularJS for web and mobile frontend development. Many AngularJS developers recognize the advantages of shifting to Angular, but because the migration process is elaborate, they hesitate to make the switch. Even so, the many new features added in each version of Angular makes upgrading the right decision for most organizations.

### Nine reasons to upgrade to Angular

The following are nine reasons it makes sense to migrate from AngularJS to Angular for creating modern-day applications.

  1. **Architecture:** AngularJS's notions of range and controllers are stiff and difficult to reuse. Angular is based on a pecking order of components and services. It allows you to reuse elements while increasing their testability and maintainability.

  2. **Framework:** AngularJS is versatile but much less secure and manageable than Angular. Angular enforces a structured, component-based methodology, which is an accurate method of exchanging information between elements. Therefore, producing and maintaining larger applications is seamless in recent versions of Angular.

  3. **Language:** AngularJS utilizes the old, familiar JavaScript, which makes it very easy to learn how to do a task. However, because there is not a type-checking feature, compile-time mistakes go unnoticed. Angular takes advantage of the uniformity and flexibility of the TypeScript language. It enhances code, decreases runtime errors, and works in multiple systems. TypeScript also provides backward compatibility with JavaScript and offers higher protection and helps identify errors earlier in code production.

  4. **Mobile assistance:** AngularJS was not created specifically for mobile apps. Angular 5 and later versions support [service workers][5], a key component of [progressive web apps][6]. While you could use Ionic or a similar framework for mobile support in AngularJS, it could impact user experience. The modular layout of the Angular 7 framework dramatically decreases its memory footprint on mobile devices.

  5. **Material Design:** Angular 5 introduced the [Component Dev Kit][7] (CDK), the core of Angular's product element library, which enables development teams to create user interface (UI) components. Angular 7 integrates naturally with [Material Design components][8], which enable the development of responsive and multi-platform applications. These UI improvements are a major reason organizations decide to migrate to Angular.

  6. **Speed:** AngularJS is an efficient framework, but the code tends to be slow-moving in large applications due to the wider variety of ranges and bindings. Angular 6 introduced Ivy, a new production engine that provides faster compilation, decreased package size, better debugging, greater versatility, and reverse-compatibility.

  7. **Data binding:** AngularJS's two-way data binding can create holdups and traffic jams in development. Angular [template syntax features][9], including property binding, event binding, template statements, interpolation, and more, improve overall application efficiency and information exchange operating speed.

  8. **Tooling support:** AngularJS depends on third-party IDEs like [WebStorm][10], while Angular takes advantage of the command-line interface (CLI). This minimizes the time invested in creating an application. Developers also can include Angular entities such as files or Angular-specific things like elements, components, solutions, and regulations.

  9. **Scheduled updates:** Angular aims to provide optimum stability for critical applications, so it releases updates on a regular, six-month cycle.




Upgrading from AngularJS to Angular offers significant advantages. Whether your goal is improving customer experience, developing progressive web apps, reusing code, or all of these, the most recent variations of Angular should meet your needs.

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/8/upgrade-angular

作者：[Alex Vasylenko][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/avacodes
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/blocks_building.png?itok=eMOT-ire (Blocks for building)
[2]: https://angularjs.org/
[3]: https://angular.io/
[4]: https://insights.stackoverflow.com/survey/2020#technology-web-frameworks
[5]: https://angular.io/guide/service-worker-intro
[6]: https://en.wikipedia.org/wiki/Progressive_web_application
[7]: https://material.angular.io/cdk/categories
[8]: https://material.angular.io/
[9]: https://angular.io/guide/template-syntax#more-on-template-syntax
[10]: https://www.jetbrains.com/webstorm/
