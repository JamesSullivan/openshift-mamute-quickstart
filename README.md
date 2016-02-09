
## Quickstart to run Mamute on OpenShift -- Experimental ##

#### Assumes you already know how to set up Mamute and does not explain all steps ####

#### Java 1.8 and Mamute 1.4.0 ####


1. First create an OpenShift DIY application with your desired appname (here, using "openshiftmamute"):
```
rhc app create openshiftmamute diy
```

2. Add git remote to openshiftmamute quickstart and pull code from it.
```
cd openshiftmamute
git remote add upstream https://github.com/JamesSullivan/openshift-mamute-quickstart.git
git pull -s recursive -X theirs upstream master
```

3. Read the `.openshift/action_hooks/start` file carefully and change as appropriate, particlarly the ftp address of the mamute-1.4.0.war file that you want to use. The latest version of mamute-1.4.0.war includes the code needed to be able to bind to OPENSHIFT_DIY_IP. Then push the code to OpenShift. 

```
git push
```

this will take a while as it sets up Java 8, etc.


4. Add mysql database from the web console
   go to https://openshift.redhat.com/app/console/applications then click on openshiftmamute
   select  Add MySQL 5.5
   Set up MySQL, create database mamute_development with permissions (included script uses user: test password: mysql) but change according to your own Mamute build

5. Start by using `rhc ssh -a openshiftmamute` into your app the `cd ${OPENSHIFT_DATA_DIR}mamute` and run `./run.sh`
   This will allow you to see any problems 

6. Check that Mamute is up and running by going to http://openshiftmamute-{domain}.rhcloud.com. Replace {domain} with your own domain name.


