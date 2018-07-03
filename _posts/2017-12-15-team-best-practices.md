---
title:  "Team Best Practices"
date: 2018-01-01
categories: Practices
tags: best-practices
---

## Branching models
There are two options that are used on our projects:
1. [GitFlow][link_gitflow] is used for complicated solutions with a strict release, beta and other special rules.
2. [GithubFlow][link_githubflow] ([translation][link_githubflow_ru]) is used when we need the most simple and transparent code flow.

### GitFlow
1. `master` branch is used only for released sources.
2. `develop` branch is used for development purposes.
3. `feature` branch is used for new features.
4. `bugfix` branch is used for bugfixes.
5. Direct commits to `master|develop` are not allowed.
6. Every change should be done by pull request.
7. Also, tags can be used for special cases.
8. Development process starts from branch creation from `develop`.

#### Branch naming and commit messages
1. `feature|bugfix` branch have `feature|bugfix/JIRAID-short-description` naming pattern. This practice allows to link every branch and pull request with git history.
2. Commit messages should follow `component-that-you-are-working-on: actual changes` pattern. Example: `user-form: add registration link`.

### GitHubFlow
1. `master` branch is used as a main *stable* branch.
2. Direct commits to `master|develop` are not allowed.
3. Every change should be done by pull request.
4. Also, tags can be used for special cases.
5. Additional branches (`staging`, `uat`, etc.) can be created for deployment purposes.
6. Development process starts from branch creation from `master`.

#### Branch naming and commit messages
1. Branches do not have strict naming rules except `branch-name` pattern.
2. Commit messages should follow `JIRAID component-that-you-are-working-on: actual changes` pattern. Every commit should contain a link to corresponding JIRA ticket.

## Pull requests and code review
It is *required* to push your code by pull requests and *every* pull request should be reviewed by two or more team members. This practice is used to:

1. Share knowledge, code style and coding practices in both directions.
2. Avoid bugs and unclear and hard-to-understand code.
3. Build artifacts, run tests and linters for changed code.
4. Store clear changelog in git commit history.

Pull request name should follow `JIRAID: short description\n\nDetailed explanation[optional]` pattern.

### How to work in your feature branch
In case if you need to implement some big feature and working in your own feature branch sometimes happens that when your pull request is ready on Github you see that there are some conflicts between your branch and develop which will be difficult to resolve since you are working in your own branch for a couple of days/weeks and a lot of files have changed in both branches. To prevent this situation it is useful to merge every accepted pull request in develop branch or merge at least every a couple of days develop into your feature branch. This approach allows:

1. Prevent difficult and time consuming merge with target branch.
2. Keep the code up to date and use all newly implemented features in your code.

## Continuous Integration / Continuous Delivery
Every project should have its own CI/CD jobs and this approach gives:

1. Automated static code analysis, build and test `develop|master` branches for any change.
2. Automated static code analysis, build and test for every pull request and notify source control system with its results.
3. Automated delivery from certain branches to any certain environment. Code that sits in git and was not delivered to users is useless and makes nobody happy.
4. Freedom from thoughts: "does my code pass tests and quality check, how to deliver my changes to users".
5. Transparent development workflow, so developers can concentrate only on features and does not spend time on stuff that definitely should be automated.

Usually we use Jenkins (especially [jenkins pipelines][link_jenkins_pipeline]) or TeamCity ([Automatic bootstrapper][link_teamcity]) for CI/CD purposes. These tools cover all requirements, has a lot of useful and open-source plugins and it is free.

## Static code analysis
Every platform and language has its own great tools for static code analysis: [eslint][link_eslint] for JS, [rubocop][link_rubocop] for Ruby, [lint][link_android_lint] for Android Studio and etc. So please configure and use this tools in your coding workflow and follow its recommendations and rules.
Also, there are great tools such as [SonarQube][link_sonarcube] that can do static code analysis, find potential bugs, calculate technical debt, visualize a lot of statistics for almost every language. It helps improve your coding skills and projects overall that you are working on. So configure SonarQube on your projects (in case if it was not done yet) and be happy! :smile:

## Tests
We greatly recommend writing unit- and integration tests for your code because:
1. It is a great documentation for your code.
2. It does not allow to break existing code.
3. Any developer can change any piece of code without fear and be sure that everything is working as expected and even better!
4. The code is written faster so you have more time for cookies.
5. The team can (should) establish certain requirements for test coverage on CI server.

## Versioning
[Semantic Versioning][link_semversioning] is a great practice for transparent and clear product versioning. It is flexible and satisfies almost any product requirements.

## Communication
Usually, we use:
1. Slack or Skype for real-time communication and notifications from services.
2. Emails for more official and important messaging.
3. JIRA/Github as progress, time and task tracking system.

It is important to have a real-time vision of plan, state, and progress of the whole company and to reach this goal we have to track our progress, notify about changes and resolve concerns as soon as possible. Described communication and tracking systems allow us to do this, so do not sit and wait when your concern will be resolved or you will be asked about it but ask and let others know. This is how [reactive systems][link_reactive_systems] work and we have to behave the same way.

## Our developer community
It is nice to know that you are not alone and can share your knowledge and ask your teammates for help. We set up technical-minutes (15 minute meeting a couple times a week) to share, discuss or ask about something. Also, we have slack channels for this purposes so in case if you know or want to know something useful - feel free to contact with teammates! :smile:

## Being professional (off-top)
To be a good professional you have to learn, analyze, use best practices, methods and techniques and **share** your knowledge with others. But being professional does not mean only write beautiful code and unit tests, have a lot of experience in Java or JS, it means that you don't try but just **do**, take **responsibility** for what you are doing and remember:

<p align="center">
  <img src="http://i3.kym-cdn.com/photos/images/facebook/000/933/845/c3a.jpg" alt="responsibility" width="300"/>
</p>

[link_gitflow]: http://nvie.com/posts/a-successful-git-branching-model/
[link_githubflow]: https://lucamezzalira.com/2014/03/10/git-flow-vs-github-flow/
[link_githubflow_ru]: https://habrahabr.ru/post/189046/
[link_jenkins_pipeline]: https://jenkins.io/doc/book/pipeline/
[link_eslint]: http://eslint.org/
[link_rubocop]: https://github.com/bbatsov/rubocop
[link_android_lint]: https://developer.android.com/studio/write/lint.html
[link_semversioning]: http://semver.org/
[link_reactive_systems]: https://gist.github.com/staltz/868e7e9bc2a7b8c1f754
[link_teamcity]: https://git.itransition.com/projects/PROJECTALUDE/repos/teamcity-bootstrap/browse
[link_sonarcube]: https://git.itransition.com/projects/PROJECTALUDE/repos/sonar/browse
