cakephp-howto
=============

Some methods about cakephp.


<h3>Use a model in a controller</h3>
	public $helpers = array('Html', 'pluginName.OtherHelperName');

<h3>Use a component in a controller</h3>
	public $components = array('Session', 'pluginName.OtherComponentName);

</h3>Use a helper in a controller</h3>
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

<h3>格式化数据库结果集（去掉Model层）</h3>
	============对单一Model层的结果集==========
	App::uses('Hash', 'Utility');
 	$record = Hash::extract($record, '{n}.User');
	或
	$record = current($record);

	============对多个Model层的结果集（利用字段别名避免相同字段名）==========
	App::uses('Hash', 'Utility');
	$record = Hash::merge(Hash::extract($record, '{n}.User'), Hash::extract($record, '{n}.School'));





