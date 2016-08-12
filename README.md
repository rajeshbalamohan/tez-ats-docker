
Still Work In Progress. Will update soon.

Initial version of docker based tez analyzer (0.9.x) with Zeppelin (0.6.x).

Steps to install:
================
1. Install docker
2. Clone this repository
3. "docker build -t tez/analyzer:0.1 zeppelin/"
4. "docker run -p 12000:11000 -v /tmp/docker/conf:/usr/local/zeppelin/conf -v /tmp/docker/logs:/usr/local/zeppelin/logs -v /tmp/docker/dagFiles:/dagFiles -i <IMAGE_ID>"
where IMAGE_ID is the id generated during the build.  "/tmp/docker" is the place where you cloned this repository. Basically conf, logs, dagFiles are directories
which can are mapped to local file system.
5. Place the imported ATS data in dagFiles directory.
6. Open "http://machine:12000/"
7. Import notebook "Tez_ATS_JobAnalyzer.json". Replace "dagName" with the dagName you are planning to analyze with.
8. Please note that latest Tez 0.9/Hive master has got some issues in populating ATS. This has been tested with HDP 2.3/2.4 builds.

This is still WIP. Will update with more details soon.

