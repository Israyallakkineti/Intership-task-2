Started by user Israyal
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/lib/jenkins/workspace/sample
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Checkout)
[Pipeline] git
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git rev-parse --resolve-git-dir /var/lib/jenkins/workspace/sample/.git # timeout=10
Fetching changes from the remote Git repository
 > git config remote.origin.url https://github.com/Israyallakkineti/just.git # timeout=10
Fetching upstream changes from https://github.com/Israyallakkineti/just.git
 > git --version # timeout=10
 > git --version # 'git version 2.43.0'
 > git fetch --tags --force --progress -- https://github.com/Israyallakkineti/just.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 159c66c5aaefd4f582af90574ed54248841873fe (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 159c66c5aaefd4f582af90574ed54248841873fe # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git branch -D main # timeout=10
 > git checkout -b main 159c66c5aaefd4f582af90574ed54248841873fe # timeout=10
Commit message: "first commit"
 > git rev-list --no-walk 159c66c5aaefd4f582af90574ed54248841873fe # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Docker Image)
[Pipeline] sh
+ docker build -t jenkins-ci-cd-demo .
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 144B 0.0s done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/node:16
#2 DONE 0.3s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s

#4 [1/5] FROM docker.io/library/node:16@sha256:f77a1aef2da8d83e45ec990f45df50f1a286c5fe8bbfb8c6e4246c6389705c0b
#4 DONE 0.0s

#5 [internal] load build context
#5 transferring context: 4.73kB 0.0s done
#5 DONE 0.0s

#6 [2/5] WORKDIR /app
#6 CACHED

#7 [3/5] COPY package*.json ./
#7 CACHED

#8 [4/5] RUN npm install
#8 CACHED

#9 [5/5] COPY . .
#9 DONE 0.1s

#10 exporting to image
#10 exporting layers 0.1s done
#10 writing image sha256:61ba9cccda882026d322c16b4aaed08225fe65c9d182ad75e5fde0c772a5d739 done
#10 naming to docker.io/library/jenkins-ci-cd-demo 0.0s done
#10 DONE 0.1s
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Run Container)
[Pipeline] sh
+ docker run -d -p 3000:3000 jenkins-ci-cd-demo
2cc3c659fc3375d6ebfa76c1563d24cbfc92aa7581365b7418f88237fa4dfa90
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
