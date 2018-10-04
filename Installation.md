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
- Visit http://localhost:9000 and create an admin account with the access-token you see in the output of that command
- The map will start at 0,0 (blue ocean)
- Click Dashboard -> Settings and edit the start location
- RDM is now running on your system 🍻 
- (you can now press Ctrl-C to stop in attached mode and start it again with `docker-compose up -d rdm`

# Installing Images
## On Linux
- find the volume name: `docker volume ls` (usually named `rdm_image` or `realdevicemap_image`)
- find it's "Mountpoint" `docker volume inspect rdm_images`
- add images to egg, gym, pokemon, pokestop and unkown_egg in there <br>
  example images can be found [[here|https://cdn.discordapp.com/attachments/473886293647163412/496422771656622091/example_images.zip]] (extract all contents from example images into the volume path) (Icons by [[Icons8|https://icons8.com/]])
- restart rdm to create raid images (`docker-compose down && docker-compose up -d` from the compose/rdm folder)

## On MacOS
- stop rum `docker-compose down`
- edit `docker-compose.yml`<br>
change `images:/perfect-deployed/realdevicemap/resources/webroot/static/img` <br>
to `- /absolut/path/to/images:/perfect-deployed/realdevicemap/resources/webroot/static/img`
- go to that folder (e.g.: `/absolut/path/to/images`) 
- add images to egg, gym, pokemon, pokestop and unkown_egg in there <br>
  example images can be found [[here|https://cdn.discordapp.com/attachments/473886293647163412/496422771656622091/example_images.zip]] (extract all contents from example images into the volume path) (Icons by [[Icons8|https://icons8.com/]])
- restart rdm to create raid images (`docker-compose down && docker-compose up -d` from the compose/rdm folder)

## On Windows
- TODO

### Continue with the Installation of one of the compatible RDM-API Device Controllers
- [[RealDeviceMap-UIControl|https://github.com/123FLO321/RealDeviceMap-UIControl]]<br>
      requires a Jailbroken iOS Device with Poke++ and MacOS (or VM) with Xcode