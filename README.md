# publish-3p-ivy

Use this bare bones project to publish third-party dependencies to our internal Ivy repository.  This project simply contains the ivy boilerplate needed to perform such a task.

## How to use it

1. Run the [create-ivy-project](https://shared-jenkins.mc.wgenhq.net/jenkins/job/create-ivy-project/) Jenkins job to create the necessary directories in the Ivy repo where your artifact will reside. **NOTE:** directory names (i.e. organization and module names) must not contain '.' or publish will fail inexplicably; conventionally we use '-' in our directory names.
2. Add your artifact (e.g. a Java jar file) to /build/artifacts/
3. Modify [ivy.xml](https://github.com/amplify-education/publish-3p-ivy/blob/master/ivy.xml)
 1. Change the values for the **organization** and **module** attributes of the \<info\> element to match those that you entered as parameters to the **create-ivy-project** Jenkins job.
 2. Change the **version** attribute value of the \<info\> element as needed.
 3. Change the **artifact** name to that of your artifact filename (without the extension). **NOTE:** if your artifact has a version number in the filename (e.g. "-2.0" in javax.ws.rs-api-2.0.jar), rename the file such that it doesn't contain the version (ivy will automatically be appending the version to the artifact name upon publish)
4. Commit and push your changes
5. Run the [publish-3p-ivy](https://shared-jenkins.mc.wgenhq.net/jenkins/job/publish-3p-ivy/) Jenkins job
