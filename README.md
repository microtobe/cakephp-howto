cakephp-howto
Some methods about cakephp
=============

<h3>Use a model in a controller (normal)</h3>
	public $helpers = array('Html', 'pluginName.OtherHelperName');

<h3>Use a component in a controller (normal)</h3>
	public $components = array('Session', 'pluginName.OtherComponentName);

<h3>Use a helper in a controller (normal)</h3>
	public $uses = array('User', 'pluginName.OtherModelName');

<h3>Use a model in a action</h3>
	$this->modelName = $this->loadModel('pluginName.modelName');

<h3>Use a model in any place</h3>
	$this->modelName = ClassRegistry::init('pluginName.modelName');

<h3>Use a component in a action</h3>
	$this->componentName = $this->components->load('pluginName.componentName');

<h3>Use a component in a other component</h3>
	$components = array('pluginName.componentName');

<h3>Use a component in any place</h3>
	App::uses('SomeComponent', 'pluginName.Controller/Component');
	$this->Some = new SomeComponent(new ComponentCollection());

<h3>Use a helper in a action</h3>
	$this->helpers[] = 'Html';

<h3>Use a helper in a other helper</h3>
	$helpers = array(‘Html’);

<h3>Use a action in a any place</h3>
	App::uses('SomeController', 'pluginName.Controller');
	$someController = new SomeController();
	$someController->someAction();


<h3>字段自增</h3>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('count' => $dboSource->expression('count = count + 1')));

<h3>字段函数比较</h3>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$conditions[] = $dboSource->expression('INET_ATON(version) > INET_ATON("' . $version . '")');

<h3>字段开关</h3>
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('active' => $dboSource->expression('IF(active = "y", "n", "y")')));

<h3>区分DataSource打印sql记录</h3>
	App::uses('ConnectionManager', 'Model');
	ConnectionManager::getDataSource('default')->showLog();
	ConnectionManager::getDataSource('master')->showLog();

	
<h3>格式化数据库结果集</h3>
	============去掉Model层（单一Model层）==========
	App::uses('Hash', 'Utility');
 	$record = Hash::extract($record, '{n}.User');
	或
	$record = current($record);

	============对多个Model层合并到同一层（利用字段别名避免相同字段名）==========
	App::uses('Hash', 'Utility');
	$record = Hash::merge(Hash::extract($record, '{n}.User'), Hash::extract($record, '{n}.School'));





