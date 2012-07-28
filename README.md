This is Mobiliser.  
Deploy from git, separating project and system policy


License
-------

Copyright 2012 Andrew Aylett

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

Motivation
----------

There are many deployment tools available today, so why create another?

Mobiliser is intended to allow you to deploy your project where it's needed,
without faffing about.  It's USP is separation of project and system policies
from the mechanics of deploying -- while many existing deployment projects
allow a split between policy and mechanism, Mobilise breaks policies into a
project part (for example, project name and type) and a system part (for
example, database connection information for a particular project).  This
split is intended to keep environment-specific information out of the project
source, allowing it to be separately versioned.

Mobilise also recognises that source code should be accessible to the
developer.  Checking out the source should enable a development environment to
be set up without having to edit files that are stored in the repository: when
deploying to an environment, any necessary changes will be made.

Mobiliser is intended to be used from the post-receive hook of a git
repository, but will be usable directly too.

User Stories
------------

### Static HTML ###

Ann develops using raw HTML.  Mobiliser helps her by verifying that her HTML
is correct and by putting the files into the right place on the server,
ensuring that deployment is atomic.

### Wordpress ###

Bob develops Wordpress sites.  Mobiliser helps him by allowing him to run
Wordpress out of his working copy locally, while ensuring that the right URLs
are set and the right database is used when he deploys to production.

### Wordpress theme ###

Carole develops Wordpress themes.  Mobiliser helps her by deploying her theme
into a fully-functional templated Wordpress site.

### Multiple Environments ###

Dave needs to get sign-off from his client before pusing changes to
production.  Mobiliser help him by letting him push to a UAT environment for
sign-off before deploying to production.

### Java WAR ###

Eve develops using Java.  Mobiliser helps her by running her build scripts and
unit tests before deploying her project to the right servlet container.

### Python WSGI ###

Fred develops using Flask.  Mobiliser helps him by managing his service
configuration when he deploys.


Design Goals
------------

* No request left behind: deployments should be atomic.
* Environment Agnostic Projects: Projects shouldn't contain any information
  that might change when moved to a different server.
* Versioned policy: Project policies belong with the project source, system
  policies can all be version controlled together.
* Project Agnostic System Policy: System policy should be independant of
  project code: it has to know the type of the project, and provide the
  correct configuration for that type's mechanism.
* Convention based mechanisms: It's OK if a mechanism depends on the project
  being laid out in the 'right' way.
* Server control: Mobiliser deploys sites into web servers.  It will be
  possible to fully deploy a new site for the first time, modulo DNS changes.
* Easy QA: It should be possible to populate databases for a QA environment --
  possibly directly from prod?

Current Status
--------------

As you can see: no code yet.
