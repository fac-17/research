# Continuous integration




## Definition

Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.

quote
“Continuous Integration doesn’t get rid of bugs, but it does make them dramatically easier to find and remove.”
— [Martin Fowler, Chief Scientist, ThoughtWorks](https://www.martinfowler.com/articles/continuousIntegration.html)

![](https://i.imgur.com/CaNWdSW.png)

The whole idea is that nobody is working on a code base that deviates significantly from anyone else’s. Continuous Integration means the team knows what the current state of the code truly is, we avoid big risky merges, and people can refactor as much as they need to.

Contrary to popular belief, continuous integration is an attitude, not a tool. It's a shared agreement by the team that:

1.When we get the latest code from the repository, it will always build successfully and pass all tests.
2.We will check in our code every two to four hours.

There's lots of ways to make this happen, but they tend to be a variation on this theme:

3. Before check-in, run the build and tests and make sure they pass.
4. Tell people not to update from the repository because you're doing an integration.
5. Check in.
6. Go to a different machine (often a dedicated "integration machine"), get the latest code from the repository, and make sure latest changes build and pass there, too.
7. Done--tell people they can update again.


It's part of a bigger idea of continuous delivery:

![](https://i.imgur.com/wBlN6F7.png)


## Who is Travis?

![](https://media.giphy.com/media/xT1Ra40M1XG7BSjXBS/giphy.gif)

![](https://media.giphy.com/media/L7cVrIkAfdEhW/giphy.gif)

![](https://media.giphy.com/media/14lRMUFXsg3voc/giphy.gif)


As a continuous integration platform, Travis CI supports your development process by automatically building and testing code changes, providing immediate feedback on the success of the change. Travis CI can also automate other parts of your development process by managing deployments and notifications.

## What can Travis do?



When you run a build, Travis CI clones your GitHub repository into a brand-new virtual environment, and carries out a series of tasks to build and test your code. If one or more of those tasks fail, the build is considered broken. If none of the tasks fail, the build is considered passed and Travis CI can deploy your code to a web server or application host.


![](https://i.imgur.com/Yq3C7O7.png)

## Example 

![](https://i.imgur.com/ObiGUZa.png)

![](https://i.imgur.com/WjnwmIL.png)


## Why?

By integrating regularly, you can detect errors quickly, and locate them more easily.

Because you’re integrating so frequently, there is significantly less back-tracking to discover where things went wrong, so you can spend more time building features.

## How?

![](https://media.giphy.com/media/l4pT1eIWDh3pOnB3G/giphy.gif)

Trigger integration tests on a merge to the master branch in git. 

Execute a set of tests.

Declare that the code integrated successfully or not.

For compiled languages, there are default tests.

For scripting languages like Python or Javascript, developers must create their own.

## Resources

[Defintion](https://www.thoughtworks.com/continuous-integration)
[Noobs Guide: Continuous Integration & Continuous Delivery](https://medium.com/@brenn.a.hill/noobs-guide-continuous-integration-continuous-delivery-continuous-deployment-d26ac4f2beeb)
[Introduction to Continuous Integration & Continuous Deployment](https://medium.com/pulseque/introduction-to-continuous-integration-continuous-deployment-38c3ebc07221)
[Continuous Integration - Martin Fowler](https://martinfowler.com/bliki/ContinuousIntegrationCertification.html)
[Travis (not the band)](https://travis-ci.org/)
[DWYL](https://github.com/dwyl/learn-travis)
