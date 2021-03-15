# Generic parent project

The parent POM project can be extended by all java based projects.
The goal is, in a micro services world, if we maintain a single parent project and allow all shared libraries repo
or microservices repo to extend the same, you could achieve the following -

1. Consistent dependency versions. All library versions upgraded controlled in one place.
2. Plugin management and configuration can be made in one single place. In this example, you might note, there are
   multiple plugins such as checkstyle, duplicate finder and so on. This helps in -
   - Consistent code linting via checkstyle (as an example). So that all repos follows similar coding style.
   - Plugins such as duplicate finder allows to keep one single consistent library as dependency.
   - Dependency analyzer makes sure all dependencies in each module are explicitly declared, so that your code do not
      cause issues because of using transitive dependencies unknowingly.
   - Spotbugs to find any code issues.
   - Enforce banned dependencies from being used in any of projects extending this as the parent project.
   - POM tidy plugin.

# Disadvantages of using a single parent POM project
Of course, there are disadvantages by enforcing all repos to use a single parent maven project.
   - It might be too prescriptive for some teams.
   - Dependency version upgrade should be carefully done as all of these are controlled from a single parent project.
     An efficient build pipeline is needed
