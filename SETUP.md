# Setup Bun

## Installation

### macOS/Linux (curl)

```shell
$ curl -fsSL https://bun.sh/install | bash # for macOS, Linux, and WSL
# to install a specific version
$ curl -fsSL https://bun.sh/install | bash -s "bun-v1.0.0"
```

### NPM

```shell
$ npm install -g bun # the last `npm` command you'll ever need
```

### Homebrew

```shell
$ brew tap oven-sh/bun # for macOS and Linux
$ brew install bun
```

### Docker

```shell
$ docker pull oven/bun
$ docker run --rm --init --ulimit memlock=-1:-1 oven/bun
```

### Proto

```shell
$ proto install bun
```

## Quickstart

Let's write a simple HTTP server using the built-in Bun.serve API. First, create a fresh directory.

```shell
mkdir project_name
cd project_name
```

Run bun init to scaffold a new project. It's an interactive tool; for this tutorial, just press enter to accept the default answer for each prompt.

```shell
bun init
```

### Run a script

Bun can also execute "scripts" from your package.json. Add the following script:

```json
{
  "name": "quickstart",
  "module": "index.ts",
  "type": "module",
  "scripts": {                      // HERE
    "start": "bun run index.ts"     //
  },                                //
  "devDependencies": {
    "bun-types": "^0.7.0"
  }
}
```

Then run it with bun run start.
```shell
$ bun run start
```

### Install a package

Let's make our server a little more interesting by installing a package. First install the figlet package and its type declarations. Figlet is a utility for converting strings into ASCII art.

```shell
$ bun add figlet
$ bun add -d @types/figlet # TypeScript users only
```

Update index.ts to use figlet in the fetch handler.

```Typescript
import figlet from "figlet";

const server = Bun.serve({
  fetch() {
    const body = figlet.textSync("Bun!");
    return new Response(body);
    return new Response("Bun!");
  },
  port: 3000,
});
```
Restart the server and refresh the page. You should see a new ASCII art banner.

## Postman

We will be using postman to test out our routes.

Now you're ready to start the workshop!
