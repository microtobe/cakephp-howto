cakephp-howto
=============

Some methods about cakephp.........

<a class="anchor" href="#use-a-model-in-a-action">Use a model in a action</a>.

Use a helper in a action.

Use a component in a action.

<a class="anchor" href="#use-a-model-in-any-place">Use a model in any place</a>.

Use a helper in a other helper.

Use a component in a other component.








<h2>Use a model in a action</h2>
$this->modelName = $this->loadModel('pluginName.modelName');




<h2>Use a model in any place</h2>
$this->modelName = ClassRegistry::init('pluginName.modelName');