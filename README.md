# LibPQ - detach your M code from workbooks and reuse it!

This project offers a collection of functions and useful queries for Power
Query Formula Language (also known as M language) and a loader to import source
code from external modules into Power Query.

#### Feature highlights

- Import source code from plain text files located on disk or on the web
- Unlimited number of import locations ordered by priority
- [Unit testing][unittesting] framework
- Show [docstrings] in Power Query user interface
- A collection of general purpose [functions and queries][modules]
- Compatibility with [@tycho01's library][tycho01]
- [Automated test execution][CI] before merging any changes to this project

#### More information

- [Introductory overview][intro] is available at author's blog
  along with several [other articles](https://potyarkin.com/tags/libpq/) on LibPQ
- [Documentation][docs] describes some more specific use cases
- [Release notes](RELEASES.md) contain important information on latest LibPQ changes
- [Roadmap](ROADMAP.md) describes project vision and plans for the future

#### What other people say about LibPQ

- Roger Torné: [Reutilizar funciones en Power Query de Excel](http://blog.blauservices.com/?p=1963) (in Spanish)
- Twitter highlights:
    [Jay Killeen](https://twitter.com/jaykilleen/status/959979020245917696),
    [Maxim Zelensky](https://twitter.com/Hohlick/status/960030006750703616)

[intro]: https://potyarkin.com/posts/2018/expanding-power-query-standard-library-introducing-libpq/
[tycho01]: https://github.com/tycho01/pquery
[docstrings]: Docs/Docstrings.md
[docs]: Docs/README.md
[CI]: CI/README.md

## Installation and usage

#### Copy source code to the filesystem (optional)

Download the [contents of this repo][zip] and extract it anywhere you want. If
you skip this step you will not be able to list all available modules with
`LibPQ()` call and every time you load a module LibPQ will access the network.

#### Add LibPQ to the workbook

Create two blank queries in your workbook:

- **LibPQ** - copy the contents of [LibPQ.pq](LibPQ.pq) verbatim
- **LibPQPath** - provide location of modules source code (local and/or web).
  See sample at [LibPQPath-sample.pq](LibPQPath-sample.pq)

#### Import LibPQ modules when writing your queries

Import any of the available modules via `LibPQ("modulename")` when writing your
queries in Advanced Editor.

To import all modules available locally use `LibPQ()` with no arguments (or
`null`). That will return a record where keys are module names and values are
the results of loading those modules (function object or output of a query).

[zip]: https://github.com/sio/LibPQ/archive/master.zip

## LibPQ modules
All modules are grouped into namespaces, much like the standard library:

- **Date** - Functions for working with dates
- **Factory** - Functions that create other functions
- **Folder** - Functions for manupulating folders and their contents
- **Function** - Functions that operate on other functions
- **List** - Functions for working with lists
- **Module** - LibPQ tools for importing source code
- **Read** - Functions that import data
- **Table** - Functions for table operations
- **Tests** - Unit tests for LibPQ modules
- **Text** - Functions for working with text
- **[UnitTest][unittesting]** - Unit testing framework

Detailed [module list][modules] is available in documentation, and each module
has a clear description in the comment at the top of its source file.

[modules]: Docs/Modules.md
[unittesting]: Docs/UnitTesting.md

## Compatibility with @tycho01's library

LibPQ allows specifying multiple possible locations for source code, that's why
you can add [@tycho01's library][tycho01] as a fallback.

Any module from that library should be supported, though some will require
adding a `Load` query to your workbook. To create a `Load` alias for `LibPQ`
you need to:

- Create a new blank query
- Replace all its code with text `LibPQ`
- Save the query under the name `Load`

Now the `Load` function will be available from `#shared` context, and you
should be able to import any module from [@tycho01's library][tycho01].


## Contributing

All contributions are welcome!
Please check [CONTRIBUTING.md](CONTRIBUTING.md) for details


## Support

#### Issue tracker

GitHub's [issue tracker] is the primary venue for asking and answering support
questions. Please don't forget to search closed issues for the topic you're
interested in!

If you know an answer to the question asked by someone else, please do not
hesitate to post it! That would be a great help to the project!

#### Email

If for some reason you'd rather not use the [issue tracker], contacting me via
email is OK too. Please use a descriptive subject line to enhance visibility
of your message. Also please keep in mind that support through the channels
accessible to the public is preferable because one answer can help many people
who might read it later.

My email is visible under the GitHub profile and in the commit log.

#### Community support

You might get faster and more interactive support from other users.

This project does not (yet) have a dedicated community venue, but experienced
PowerBI/Power Query users will most likely be able to figure out most common
questions. You can try asking at the local PowerBI-related forums, Facebook
groups, IRC/Discord/Telegram chats or on Reddit/StackOverflow.

[issue tracker]: https://github.com/sio/LibPQ/issues


## License and copyright

Copyright © 2017-2021 Vitaly Potyarkin
```
   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use these files except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```
