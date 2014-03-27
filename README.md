cakephp-howto
=============

Some methods about cakephp.

========================NORMAL METHODS TO USE======================

Use a model in a controller.
	public $helpers = array('Html', 'pluginName.OtherHelperName');

Use a component in a controller.
	public $components = array('Session', 'pluginName.OtherComponentName);

Use a helper in a controller.
	public $uses = array('User', 'pluginName.OtherModelName');


========================USE MODEL======================

Use a model in a action.
	$this->modelName = $this->loadModel('pluginName.modelName');

Use a model in any place.
	$this->modelName = ClassRegistry::init('pluginName.modelName');

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

========================USE EXPRESS IN SQL======================

<h1>字段自增</h1>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('count' => $dboSource->expression('count = count + 1')));

<h1>字段函数比较</h1>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$conditions[] = $dboSource->expression('INET_ATON(version) > INET_ATON("' . $version . '")');

<h1>字段开关</h1>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('active' => $dboSource->expression('IF(active = "y", "n", "y")')));

========================打印Cakephp Sql记录======================

<h1>区分DataSource打印sql记录</h1>
	App::uses('ConnectionManager', 'Model');
	ConnectionManager::getDataSource('default')->showLog();
	ConnectionManager::getDataSource('master')->showLog();










