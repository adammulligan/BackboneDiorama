# BackboneDiorama

BackboneDiorama is everything you need to build client-side web applications.
Optimised for developer happiness, it builds on the components of Backbone.js
and aims to be the easiest and the fastest way to build for the browser.

* `diorama new projectName` builds you a new project with:
  * Logical project structure for backbone components
  * Coffeescript concatenation and compilation setup
  * Backbone.js+deps and Handlebars templating included and ready for use
* `diorama generate <lots-of-stuff>` - Rails-style code generators which provide convention and structure to your projects, assist you with proven patterns and allow you to rapidly prototype. Run `diorama generate` for a full list.
* Additional lightweight libraries to plug the gaps in Backbone.js:
  * [*Backbone.Diorama.ManagedRegion*](src/lib/diorama_managed_region.md) - Memory managed view switching.
  * [*Backbone.Diorama.DioramaController*](src/lib/diorama_controller.md) - Easy switching betweens states in your application.
  * [*Backbone.Diorama.NestingView*](src/lib/diorama_nesting_view.md) - Nest Backbone.Views inside each other.
* Written entirely in and for Coffeescript, for clarity and elegance of code.

We've been using BackboneDiorama to build applications for a little while now,
but this is just the first public release. There's lots more planned (AMD
support, minification, coffeescript source maps and more generators...) and
if you've got any feedback or suggestions, we'd love to hear from you!

## Installation
Install backbone diorama as an NPM package:

    sudo npm install -g backbone-diorama

## Usage

To view the available commands, run:

    diorama help

#### Create a new project

    diorama new <ProjectName>

This will create a new diorama project inside a directory of the same
name. It creates an `index.html` file containing starting instructions.

#### Use the generators

Use generators to scaffold your code, for example:

    diorama generate collection Tasks
    diorama generate view TaskIndex

For a [complete list](src/commands/generators) of generators
available, run:

    diorama generate

#### Compiling the app

    diorama compile watch

This command watches your src/ folder for changes and compiles the
files specified in src/compile_manifest.json.
The files should be specified in the order you require them, in this
format:

```json
    [
      "collections/tasks_collection",
      "templates/task_index",
      "views/task_index_view"
    ]
```

To run the compile once without watching for changes, omit the 'watch'
argument:

    diorama compile

## Backbone.Diorama Libraries

BackboneDiorama comes with a few extra classes to compliment the
backbone stack for building complete web applications:

#### Backbone.Diorama.ManagedRegion

Creates a DOM element designed for swapping views in and out of, with
helper methods to manage unbinding events.

[Read More](src/lib/diorama_managed_region.md)

#### Backbone.Diorama.Controller

Diorama controllers are designed to coordinate views and data, and
provide entry points to certain 'states' of your application.
Routers in BackboneDiorama projects only handle URL reading and
setting, but defer to controllers for the actual behavior.

[Read More](src/lib/diorama_controller.md)

#### Backbone.Diorama.NestingView

A common pattern for Backbone applications is to nest views inside each
other. For example a collection index view where each model in the
collection gets a sub view. The advantage of this approach is that each
sub view can listen for and respond to events about a particular model,
removing the need for the collection view to be re-rendered.

Backbone.Diorama.NestingView makes it easy to stack views like this.

[Read More](src/lib/diorama_nesting_view.md)

## Development

BackboneDiorama is written in coffeescript and is packaged as an NPM
module. To install the package locally, in the project directory run:

    sudo npm install -g

This will install the diorama command onto your system. On my node
setup, this wasn't added to my PATH correctly, so check the output for a
line like:

    npm info linkStuff backbone-diorama@0.0.1
    /usr/local/share/npm/bin/diorama -> /usr/local/share/npm/lib/node_modules/backbone-diorama/bin/diorama.coffee

### Tests

Tests are written using mocha, and in the test/ folder (somewhat
unsurprisingly). Run them with:

    npm test
