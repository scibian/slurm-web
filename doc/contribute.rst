How to contribute or add page
=============================

Code style and coding rules
---------------------------

RESTAPI
^^^^^^^

The backend, developed with the Flask framework in Python, respects the PEP 8
rules.

Dashboard
^^^^^^^^^

The dashboad is built with HTML, Javascript and CSS. All the Javascript code
have been linted with ESLint. Used rules are defined in the ``.eslintrc`` file.

Code Climate
^^^^^^^^^^^^

The quality of the codebase is overseen by Code Climate. You can refer to its
summary at https://codeclimate.com/github/edf-hpc/slurm-web


Architecture Front
------------------

Design
^^^^^^

The entire front, a single page app, is designed with RequireJS, Handlebars and JQuery.

RequireJS handle the dependencies and modules loading. See RequireJS documentation
Handlebars manage the template rendering. See Handlebars documentation
JQuery help to select and perform actions on the DOM. See JQuery documentation



Directory structure
^^^^^^^^^^^^^^^^^^^

* ``dashboard/js/core`` : Application core methods, app entry point, navigation and multi-cluster mode methods
  Note : /js/core/index.js : Application entry point
* ``dashboard/js/draw`` : Draw methods for 2D and 3D canvas
* ``dashboard/js/helpers`` : Handlebars helpers used to format data
* ``dashboard/js/modules`` : Applications page
* ``dashboard/js/utils`` : Applications utils


Page API
--------

Typical module object :

.. code-block:: json

  define([
    /*
     * Require dependencies/libraries for the module
     */
  ], function (/* get the dependencies here */) {

    return function() {
      this.init = function () {
        /* perform init action like data fetching, template rendering, events binding etc... */
      }

      this.refresh = function () {
        /* set and perfom actions at refresh */
      }

      this.destroy = function () {
        /* Destroy DOM content, free memory or unbind events at destroy */
      }
    }
  })


Work with current page or add new:
----------------------------------

To add a new page in slurm-web :

* Create a module object (see above) and save it in dashboard/js/modules/(pagename)/(pagename).js
* Require the module files (.js and .hbs) in dashboard/js/core/index.js
* Add a navigation element in dashboard/js/core/navbar/navbar.js
* Add a navigation event in the `$(document).on('show')` in dashboard/js/core/index.js
