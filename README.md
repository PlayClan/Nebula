# Nebula

Generate a distribution.json for Helios.

## Usage

Nebula is not complete. The following usage is tentative.

## Commands

Commands will be documented here. You can run any command with the `--help` option to view more information.

### Init

Init commands are used for initializing empty file structures.

Aliases: [`init`, `i`]

__*Subcommands*__

---

#### Init Root

Generate an empty standard file structure.

`init root <options>`

Options:

* `--root <string>` Specify the root directory.

---

### Generate

Generate commands are used for generation.

Aliases: [`generate`, `g`]

__*SubCommands*__

---

#### Generate Server

Generate an new server in the root directory. Options are provided to include forge/liteloader in the generated server.

`generate server <id> <version> <options>`

Options:

* `--root <string>` Specify the root directory.
* `--forge <boolean>` Include forge
  * OPTIONAL (default: true)
* `--liteloader <boolean>`
  * OPTIONAL (default: false)

>
> Example Usage
>
> `generate server Test1 1.12.2 --root C:/TestRoot --forge true`
>

---

#### Generate Distribution

Generate a distribution file from the root file structure.

`generate distro [name] <options>`

Arguments:
* `name` The name of the distribution file.
  * OPTIONAL (default: `distribution`)

Options:

* `--root <string>` Specify the root directory.
* `--baseUrl <string>` Base url of your file host.

>
> Example Usage
>
> `generate distribution --root C:/TestRoot --baseUrl https://myhost.com`
>


## File Structure Setup (Tentative)

Nebula aims to provide users with an information preserving structure for storing files. The application will use this structure to generate a full distribution.json for HeliosLauncher. For coherency, the distribution structure is modularized and encapsulated by a directory pattern. These encapsulations will be explained below. They can be generated manually or by using the commands documented above.

### Distribution Encapsulation

The distribution object is represented by the main root. All command output will be stored in this directory. The structure is documented below.

Ex.

* `TestRoot` The root directory which encapsulates the distribution.
  * `servers` All server files are stored in this directory.

### Server Encapsulation

Server objects are encapsulated in their own folders. The name of the server's folder contains both its id and version.

Ex.

* `servers`
  * `TestServer-1.12.2` A server with id TestServer set to version 1.12.2.

The server directory will contain files pertaining to that server.

Ex.

* `TestServer-1.12.2`
  * `files` All modules of type `File`.
  * `forgemods` All modules of type `ForgeMod`.
  * `litemods` All modules of type `LiteMod`.
  * `TestServer-1.12.2.png` Server icon file.