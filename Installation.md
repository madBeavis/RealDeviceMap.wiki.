The follwing guide applise for RDM and can be installed everywhere (any OS that runs Docker) including away from the Workers/Xcode.

# Installation with docker-compose (install **[[Docker|https://www.docker.com/get-started]]** and [[docker-compose|https://docs.docker.com/compose/install/#install-compose]] if installed)

- Create a new folder for your compose files and RealDevieMap (example: `mkdir compose/rdm`)
- Switch into that folder (example: `cd compose/rdm`)
- Get the composer file: `wget https://raw.githubusercontent.com/123FLO321/RealDeviceMap/master/docker-compose.yml`
- Edit the file (example `nano docker-compose.yml`) <br>
  Things to change if you want to use a new db server on that instance (recommended):
  - edit the value for `DB_PASSWORD` and `MYSQL_PASSWORD` to a secure password for the rdmuser
  - edit the value for `MYSQL_ROOT_PASSWORD` to a secure password for the root user
  - if you run a db on port 3306 allready: <br>
    edit `3306:3306` to `3307:3306` for example. The db will then be accessible on the host (localhost) at port 3007 
  Things to change if you want to use a new database on an existing server:
  - TODO
- Start the Database Server (if you chose to use a new one): `docker-compose up -d db`
- Start the RealDeviceMap Server (don't add `-d` the first time so we can get the token): `docker-compose up rdm`
- Visit http://localhost:9001 and create an admin account with the access-token you see in the output of that command
- The map will start at 0,0 (blue ocean)
- Click Dashboard -> Settings and edit the start location
- RDM is now running on your system 🍻 


### Continue with the Installation of one of the compatible RDM-API Device Controllers
- [[RealDeviceMap-UIControl|https://github.com/123FLO321/RealDeviceMap-UIControl]]<br>
      requires a Jailbroken iOS Device with Poke++ and MacOS (or VM) with Xcode