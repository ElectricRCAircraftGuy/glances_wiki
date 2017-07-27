First of all, have a look [on existing plugins](http://glances.readthedocs.io/en/stable/aoa/index.html) and ask you a simple question: is it possible to improve an existing plugin instead of create a new one ? 

Second question, is it possible to use a AMP configuration ? Glances proposes [an Application Monitoring Process (AMP)](http://glances.readthedocs.io/en/stable/aoa/amps.html) where you can monitor and run action (script).

If you answer "no" to the previous questions, this page will drive you in the process of creating a new Glances plugin.

# Create an issue on the official Github to explain your need

Open an issue (feature request) in order to explain your need and how you plan to the plugin.

# Configure your development environment 

Read the following Wiki page: https://github.com/nicolargo/glances/wiki/How-to-contribute-to-Glances-%3F

# Start coding the new _foo_ plugin

foo is an example... to be replace by your plugin name.

## Create the plugin script

In the glances/plugins folder, create a glances_foo.py file. 

You can use the following skeleton: https://gist.github.com/nicolargo/505e5603217c8c4f8adf779dda558841

This skeleton is only compliant with Glances 2.x.

## Init your plugin in the main script

Edit the glances/main.py script and add the following line in the init_args method of the GlancesMain classe:

    parser.add_argument('--disable-foo', action='store_true', default=False, dest='disable_foo', help='disable Foo module')

## Add your plugin in the curses interface

Edit the glances/outputs/glances_curses.py script and add your plugin to one of the following functions (where you want the plugin to be displayed):

* self.__display_firstline
* self.__display_secondline
* self.__display_left
* self.__display_right(__stat_display)

Also add shortcut to the _hotkeys variable in the _GlancesCurses classe.

## Add your plugin in the Web interface

Create a glances/outputs/static/html/plugins/foo.html page with the following line:

    <span class="title">{{ statsCloud.getProvider() }}</span> {{ statsCloud.getInstance() }}

Add the following line to the glances/outputs/static/html/stats.html page (where you want the plugin to be displayed):

    <div class="pull-left">
        <section id="foo" ng-include src="'plugins/foo.html'"></section>
    </div>

Edit the glances/outputs/static/js/controllers.js file and insert the following line in the GlancesStats.getData function:

    $scope.statsCloud = GlancesStats.getPlugin('foo');

Edit the  glances/outputs/static/js/services/core/stats.js file and insert add the following line to the _plugins variable:

    'foo': 'GlancesPluginFoo',

Create the glances/outputs/static/js/services/plugins/cloud.js file with the following content (to be adapted to your needs):

    glancesApp.service('GlancesPluginCloud', function() {
        var _pluginName = "cloud";
        var _provider = null;
        var _instance = null;
    
        this.setData = function(data, views) {
            data = data[_pluginName];
            data = {"region": "R", "instance-type": "IT", "ami-id": "AMI", "instance-id": "IID"};
    
            if (data['ami-id'] !== undefined) {
              _provider = 'AWS EC2';
              _instance =  data['instance-type'] + ' instance ' + data['instance-id'] + ' (' + data['region'] + ')';
            }
        }
    
        this.getProvider = function() {
          return _provider;
        }
    
        this.getInstance = function() {
          return _instance;
        }
    });

And finally **generate** the public files ([read the README file](https://github.com/nicolargo/glances/blob/develop/glances/outputs/static/README.md)).

## Test 

Test your branch with both Python 2 and Python 3.

## Pull request

... on the DEVELOP branch !

The end...
