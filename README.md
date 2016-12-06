# ci-platform
CI Platform based on Jenkins 2.x

- http://artifactory.dev:8081/

  - Manual step (unless you have Artifactory Pro - https://www.jfrog.com/confluence/display/RTF/Artifactory+REST+API):
  ➜  ~ curl -u admin:password http://artifactory.dev:8081/artifactory/api/security/users
    {
      "errors" : [ {
        "status" : 400,
        "message" : "This REST API is available only in Artifactory Pro (see: http://www.jfrog.com/addons.php). If you are already running Artifactory Pro please make sure your server is activated with a valid license key.\n"
      } ]
    }%

      - Tab 'Admin'
      - Security/Groups
        - New:
            group name: deployers
            description: A group for users who perform deploys
            
      - Security/Permissions
        - New:
            name: local deployment
            groups:
              deployer -> deploy

      - Security / users
        - New:
            User name: deployer
            Email address: deployer@mail.com
            Password: deployer
        - Delete default group: reader
        - Associate user to group deployers


- http://jenkins.dev:8080/
