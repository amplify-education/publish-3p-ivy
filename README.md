# publish-3p-ivy

Use this bare bones project to publish third-party dependencies to our internal Ivy repository.  This project simply contains the ivy boilerplate needed to perform just a task.

## How to use it

1. Run the [create-ivy-project](https://shared-jenkins.mc.wgenhq.net/jenkins/job/create-ivy-project/) Jenkins job to create the necessary directories in the Ivy repo where your artifact will reside.
2. Add your artifact (e.g. a Java jar file) to /build/artifiacts/
3. Modify [ivy.xml](https://github.com/amplifylitco/publish-3p-ivy/blob/master/ivy.xml)
  1. Change the values for the **organization**, **module**, and **version** attributes of the <info> element.
  2. Change the **artifact** name to that of your artifact filename (without the extension). **NOTE:** if your artifact has a version number in the filename (e.g. "-2.0" in javax.ws.rs-api-2.0.jar), it must be removed (ivy will automatically be appending the version to the artifact name upon publish)
4. Commit and push your changes
5. Run the [publish-3p-ivy](https://shared-jenkins.mc.wgenhq.net/jenkins/job/publish-3p-ivy/) Jenkins job
