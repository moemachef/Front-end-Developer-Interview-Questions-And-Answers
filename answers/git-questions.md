# Git Questions


#### What does cherry-picking a commit with Git mean?

Cherry picking in Git means to choose a commit from one branch and apply it onto another. This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.

https://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean


#### What is Monorepo?

A monorepo is a version-controlled code repository that holds many projects. While these projects may be related, they are often logically independent and run by different teams.

#Advantages:

Visibility: everyone can see everyone else’s code. This property leads to better collaboration and cross-team contributions — a developer in a different team can fix a bug in your code you didn’t even know existed.

Simpler dependency management: sharing dependencies is trivial. There’s little need for a package manager as all modules are hosted in the same repository.

Single source of truth: one version of every dependency means there are not versioning conflicts and no dependency hell.

Consistency: enforcing code quality standards and a unified style is easier when you have all your codebase in one place.

Shared timeline: breaking changes in APIs or shared libraries are exposed immediately, forcing different teams to communicate ahead and join forces. Everyone is invested in keeping up with changes.

Atomic commits: atomic commits make large-scale refactoring easier. A developer can update several packages or projects in a single commit.

Implicit CI: continuous integration is guaranteed as all the code is already unified in one place.

Unified CI/CD: you can use the same CI/CD deployment process for every project in the repo.

Unified build process: we can use a shared build process for every application in the repo.

#Disadvantages:

Bad performance: monorepos are difficult to scale up. Commands like git blame may take unreasonably long times, IDEs begin to lag and productivity suffers, and testing the whole repo on every commit becomes infeasible.

Broken main/master: a broken master affects everyone working in the monorepo. This can be seen as either disastrous or as a good motivation to keep tests clean and up to date.

Learning curve: the learning curve for new developers is steeper if the repository spans many tightly-coupled projects.

Large volumes of data: monorepos can reach unwieldy volumes of data and commits per day.

Ownership: maintaining ownership of files is more challenging, as systems like Git or Mercurial don’t feature built-in directory permissions.

Code reviews: notifications can get very noisy. For instance, GitHub has limited notifications settings that are not best suited for a snow slide of pull requests and code reviews.


https://semaphoreci.com/blog/what-is-monorepo#:~:text=A%20monorepo%20is%20a%20version,Monorepos%20can%20reach%20colossal%20sizes.
