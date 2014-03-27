cakephp-howto
=============

Use a model in a controller (normal)
------
	public $helpers = array('Html', 'pluginName.AnyHelperName');

Use a model in a action
------
	$this->AnyModelName = $this->loadModel('pluginName.AnyModelName');

Use a model in any place
------
	$this->AnyModelName = ClassRegistry::init('pluginName.AnyModelName');

Use a component in a controller (normal)
------
	public $components = array('Session', 'pluginName.AnyComponentName);

Use a component in a action
------
	$this->AnyComponentName = $this->components->load('pluginName.AnyComponentName');

Use a component in a other component
------
	$components = array('pluginName.AnyComponentName');

Use a component in any place
------
	App::uses('AnyComponent', 'pluginName.Controller/Component');
	$this->Any = new AnyComponent(new ComponentCollection());

Use a helper in a controller (normal)
------
	public $uses = array('User', 'pluginName.AnyModelName');

Use a helper in a action
------
	$this->helpers[] = 'Html';

Use a helper in a other helper
------
	$helpers = array(‘Html’);

Use a action in a any place
------
	App::uses('AnyController', 'pluginName.Controller');
	$anyController = new AnyController();
	$anyController->anyAction();

***************

字段自增
------
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('count' => $dboSource->expression('count = count + 1')));

使用字段函数
------
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	//相同长度（"."的个数相同）的版本号比较
	$conditions[] = $dboSource->expression('INET_ATON(version) > INET_ATON("' . $version . '")');
	//active字段在[0, 1]之间转换
	$conditions['active'] = $dboSource->expression('MOD((active + 1), 2)')

字段开关
------
	App::uses('DboSource', 'Model/Datasource');
	$dboSource = new DboSource(null, null);
	$this->School->save(array('active' => $dboSource->expression('IF(active = "y", "n", "y")')));

区分DataSource打印sql记录
------
	App::uses('ConnectionManager', 'Model');
	ConnectionManager::getDataSource('default')->showLog();
	ConnectionManager::getDataSource('master')->showLog();

***************
	
格式化数据库结果集
------
	============去掉Model层（单一Model层）==========
	App::uses('Hash', 'Utility');
 	$record = Hash::extract($record, '{n}.User');
	或
	$record = current($record);

	============对多个Model层合并到同一层（利用字段别名避免相同字段名）==========
	App::uses('Hash', 'Utility');
	$record = Hash::merge(Hash::extract($record, '{n}.User'), Hash::extract($record, '{n}.School'));

*********************

关闭view试图的自动渲染
------
	如果是ajax调用action，增加$this->autoRender = false;
	如果是功能action，不需要增加$this->autoRender = false（这会关闭整个请求的视图渲染），只需要在action的最后<br />增加return; 或者 exit；



