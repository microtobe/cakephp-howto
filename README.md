cakephp-howto
=============

Some methods about cakephp.

========================NORMAL METHODS TO USE======================

<a class="anchor" href="#normal-methods-in-a-controller">Use a model in a controller</a>.
<a class="anchor" href="#normal-methods-in-a-controller">Use a component in a controller</a>.
<a class="anchor" href="#normal-methods-in-a-controller">Use a helper in a controller</a>.

========================USE MODEL======================

<a class="anchor" href="#use-a-model-in-a-action">Use a model in a action</a>.

<a class="anchor" href="#use-a-model-in-any-place">Use a model in any place</a>.

========================USE COMPONENT======================

Use a component in a action.

Use a component in a other component.

Use a component in a other helper.

Use a component in any place.

========================USE HELPER======================

Use a helper in a action.

Use a helper in a other helper.

========================USE ACTION======================

Use a action in a other action.


<h2>Normal methods in a controller</h2>
public $helpers = array('Html', 'pluginName.OtherHelperName');

public $components = array('Session', 'pluginName.OtherComponentName);

public $uses = array('User', 'pluginName.OtherModelName');



<h2>Use a model in a action</h2>
$this->modelName = $this->loadModel('pluginName.modelName');




<h2>Use a model in any place</h2>
$this->modelName = ClassRegistry::init('pluginName.modelName');