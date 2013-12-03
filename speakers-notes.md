# _Prerequisites_
1. Webpage open to `https://github.com/cloudfoundry/java-buildpack`
1. Target `https://api.run.pivotal.io`, `bhale`, `presentations`
1. Existing New Relic Service
1. Existing App Dynamics Service
1. Built `java-test-applications/java-main-application`
1. Built `java-test-applications/web-application`

---

# Automatic Container Choice
1. Push main application using `cf push`
1. Describe what is being downloaded
1. Describe the repository index and being aggressively up-to-date
1. Show that the application is now running using `http://demo-java-main-application.cfapps.io`
1. Push web application using `cf push`
1. Describe what is being download that is different from the java main application
1. Show that the application is now running using `http://demo-web-application.cfapps.io`

# Zero-touch Services
1. Bind New Relic service to java main application using `cf bind-service`
1. Re-stage the application using `cf push`
1. Describe the New Relic Agent that is being downloaded
1. Describe that the caching means that the JRE isn't being downloaded again
1. Un-bind the New Relic service from the application using `cf unbind-service`
1. Bind the AppDynamics service to the application using `cf bind-service`
1. Re-stage the application using `cf push`
1. Describe the AppDynamics Agent that is being downloaded
1. Un-bind the AppDynamics service from the application using `cf unbind-service`

# Configuring the Buildpack
1. Fork the buildpack
1. Change the `version` value in `config/openjdk.yml` to `1.7.0_40`
1. Change the java main application manifest to point at the forked buildpack
1. Re-stage the application using `cf push --reset`
1. Describe the version of OpenJDK that is being downloaded

# Extending the Buildpack
1. Add the `staging_timestamp.rb` file to the `lib/java_buildpack/framework` directory
1. Change the `frameworks` value in `config/components.yml` to add `JavaBuildpack::Framework::StagingTimestamp`
1. Re-stage the application using `cf push`
1. Show that the application now has a `staging-timestamp` system property using `http://demo-web-application.cfapps.io/system-properties`
