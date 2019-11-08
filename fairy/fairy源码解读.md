---
typora-root-url: images
---



# 开始学习

Fairy官网：[官网网址](http://www.fairygui.com/)

GitHub源码：[Unity源码网址](https://github.com/fairygui/FairyGUI-unity)

本文目录：

[TOC]





# FairyGUI编辑器的功能

### 编辑器的使用

Fairy编辑器的使用在官网【教程】中已有详细说明。

### fairy项目

用户在Fairy编辑器中创作的内容，可以独立记录在Unity项目之外。这个fairy项目存储的文件资源如下：

![编辑器内容根目录](/images/1.png)

*.fairy文件为编辑器识别的文件，打开项目的入口。

.objs文件夹内为此项目在编辑器中的缓存文件。

settings文件夹内为此项目的偏好设置，这些设置让编辑器的使用更为便捷。

项目内容被放置在assets文件夹中，其内部文件夹对应到fairy项目内部的包。

| ![fairy项目的文件资源系统中assets文件夹的内部目录](/2.png) | ![fairy项目的文件资源系统中assets/home文件夹的内部目录](/3.png) | ![fairy项目的文件资源系统中assets/home/res文件夹的内部目录](/6.png) | ![fairy项目的编辑器内资源库视图](/5.png) |
| :--------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------------------------: |
|      fairy项目的文件资源系统中assets文件夹的内部目录       |     fairy项目的文件资源系统中assets/home文件夹的内部目录     |   fairy项目的文件资源系统中assets/home/res文件夹的内部目录   |      fairy项目的编辑器内资源库视图       |

### fairy项目所记录的内容

package.xml文件标识着这个文件夹不是一个普通文件夹，而是fairy项目中的包。

它记录了此包中，包含的所有组件，包括fairy组件和资源组件。

例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<packageDescription id="f0olsc4z" jpegQuality="80" compressPNG="true">
  <resources>
    <component id="sooi0" name="main.xml" path="/" exported="true"/>
    <image id="h1cp2" name="20150827194254_2cmiy.jpeg" path="/res/"/>
    <image id="h1cp3" name="20140918195015_xrGmu.png" path="/res/" scale="9grid" scale9grid="128,192,256,384"/>
  </resources>
  <publish name="home"/>
</packageDescription>
```

除此之外，其他文件全部对应到fairy编辑器中资源库所显示的组件。

导入到fairy项目内的资源组件，如图片/音频/视频，不做处理而直接保存。

在fairy编辑器中创建的包含资源组件的fairy组件，被记录为xml文件。

这种标识fairy组件的xml文件，记录着，此组件中所有元件的信息。

例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<component size="640,1136">
  <displayList>
    <graph id="n0_sooi" name="n0" xy="0,0" size="640,1136" type="rect" fillColor="#ffcccccc">
      <relation target="" sidePair="center-center,middle-middle"/>
      <relation target="" sidePair="width-width,height-height"/>
    </graph>
    <image id="n5_h1cp" name="n5" src="h1cp3" fileName="res/20140918195015_xrGmu.png" xy="0,175" size="640,960" aspect="true">
      <relation target="" sidePair="center-center,bottom-bottom"/>
    </image>
    <component id="n2_sooi" name="n2" src="sooi1" fileName="btn1.xml" pkg="fvm90flm" xy="528,21">
      <relation target="" sidePair="right-right,top-top"/>
    </component>
    <component id="n3_h1cp" name="n3" src="h1cp1" fileName="btn2.xml" pkg="fvm90flm" xy="190,848">
      <relation target="" sidePair="center-center,middle-middle"/>
      <Button title="Start"/>
    </component>
    <text id="n6_jtlz" name="n6" xy="161,266" size="152,43" font="Microsoft YaHei" fontSize="30" text="第一行文字"/>
    <text id="n7_jtlz" name="n7" xy="161,334" size="308,82" font="Microsoft YaHei" fontSize="60" text="第二行文字"/>
    <text id="n8_jtlz" name="n8" xy="164,451" size="195,98" font="Microsoft YaHei" fontSize="30" ubb="true" text="第[size=72]三[/size]行文字"/>
  </displayList>
</component>
```

### 导出内容

fairy项目导出的内容是unity项目可用的资源。

![fairy项目的导出内容](/image-20191030195617408.png)

fairy项目中的每个包，会被导出为1个*.bytes文件，和多个图集文件。



# 提供给Unity的SDK

要在Unity中使用FairyGUI，需要置入fairy相关的两个文件夹。

fairy为多种游戏引擎提供了sdk。在Unity中使用FairyGUI，需要置入的内容：

![Fairy为Unity提供的SDK](/8.png)

## 文件夹概览

- **Resources**	Unity资源文件夹
  - **Shaders**	着色器
- **Scripts**		代码
  - **UI**		Fairy编辑器中用到的组件直接相关
  - **Event**	事件相关
  - **Filter**	滤镜相关
  - **Gesture**	手势相关
  - **Tween**	缓动相关
  - **Core**	其他fairy特色功能
  - **Utils**	为以上代码提供通用静态接口
  - **Editor**	Unity编辑器



## 主要类图

#### 可交互型组件

![类图-事件](/9.png)

#### 控制器的属性控制

![类图-Gear](/10.png)

#### 控制器的动作

![类图4](/12.png)

#### 字体

![类图3](/11.png)

#### 碰撞检测

![类图5](/13.png)



# 主要功能



## 启用FairyGUI

### FairyGUI的启用方式汇总

有两种方法加载fairy包。

#### 使用unity编辑器启用FairyGUI

将fairy提供给unity的sdk源码放入项目之后，unity识别到了其中命名为Editor的文件夹，因此扩展了自身编辑器功能。

在unity编辑器中，新增了目录 GameObject > FairyGUI > UI Panel / UI Camera 。

由此，可以在场景中创建fairy内容。

扩展编辑器的相关源码，都在FairyGUIEditor.EditorToolSet类中。

```c#
		[MenuItem("GameObject/FairyGUI/UI Panel", false, 0)]
		static void CreatePanel()
		{
#if !(UNITY_5 || UNITY_5_3_OR_NEWER)
			EditorApplication.update -= EditorApplication_Update;
			EditorApplication.update += EditorApplication_Update;
#endif
			StageCamera.CheckMainCamera();

			GameObject panelObject = new GameObject("UIPanel");
			if (Selection.activeGameObject != null)
			{
				panelObject.transform.parent = Selection.activeGameObject.transform;
				panelObject.layer = Selection.activeGameObject.layer;
			}
			else
			{
				int layer = LayerMask.NameToLayer(StageCamera.LayerName);
				panelObject.layer = layer;
			}
			panelObject.AddComponent<FairyGUI.UIPanel>();
			Selection.objects = new Object[] { panelObject };
		}
```

```c#
		[MenuItem("GameObject/FairyGUI/UI Camera", false, 0)]
		static void CreateCamera()
		{
			StageCamera.CheckMainCamera();
			Selection.objects = new Object[] { StageCamera.main.gameObject };
		}
```

#### 编写代码动态启用FairyGUI

编写代码动态加载fairy包，它将提供包内的组件和资源，之后再根据需求，创建出其中包含的组件，加入到fairy在unity中创建的根节点。

```c#
        UIPackage.AddPackage("UI/common");
        UIPackage.AddPackage("UI/home");
        GComponent winHome = UIPackage.CreateObject("home", "main").asCom;
        GRoot.inst.AddChild(winHome);
```

### StageCamera

编写代码动态启用fairy包，在操作根节点FairyGUI.GRoot时，创建了此根节点的单例。

```c#
		public static GRoot inst
		{
			get
			{
				if (_inst == null)
					Stage.Instantiate();

				return _inst;
			}
		}
```

这里，创建FairyGUI.GRoot单例时，也创建了FairyGUI.Stage的单例。

```c#
		public static void Instantiate()
		{
			if (_inst == null)
			{
				_inst = new Stage();
				GRoot._inst = new GRoot();
				GRoot._inst.ApplyContentScaleFactor();
				_inst.AddChild(GRoot._inst.displayObject);

				StageCamera.CheckMainCamera();
			}
		}
```

上面几种启用FairyGUI的方式，最终殊途同归，调用了StageCamera.CheckMainCamera方法。

```c#
		public static void CheckMainCamera()
		{
			if (GameObject.Find(Name) == null)
			{
				int layer = LayerMask.NameToLayer(LayerName);
				CreateCamera(Name, 1 << layer);
			}

			HitTestContext.cachedMainCamera = Camera.main;
		}
```

由此，创建了fairy自己的UI相机：Stage Camera。

![创建第一个fairy物件](/image-20191028144001261.png)

### Stage

使用编写代码动态启用FairyGUI的方式，会创建一个Stage物件，在Unity3D编辑器的Hierarchy视窗中，放在DontDestoryOnLoad场景中。

```c#
		public Stage()
			: base()
		{
			_inst = this;
			soundVolume = 1;

			_updateContext = new UpdateContext();
			stageWidth = Screen.width;
			stageHeight = Screen.height;
			_frameGotHitTarget = -1;

			_touches = new TouchInfo[5];
			for (int i = 0; i < _touches.Length; i++)
				_touches[i] = new TouchInfo();

			if (Application.platform == RuntimePlatform.WindowsPlayer
				|| Application.platform == RuntimePlatform.WindowsEditor
				|| Application.platform == RuntimePlatform.OSXPlayer
				|| Application.platform == RuntimePlatform.OSXEditor)
				touchScreen = false;
			else
				touchScreen = Input.touchSupported && SystemInfo.deviceType != DeviceType.Desktop;

			_rollOutChain = new List<DisplayObject>();
			_rollOverChain = new List<DisplayObject>();

			StageEngine engine = GameObject.FindObjectOfType<StageEngine>();
			if (engine != null)
				Object.Destroy(engine.gameObject);

			this.gameObject.name = "Stage";
			this.gameObject.layer = LayerMask.NameToLayer(StageCamera.LayerName);
			this.gameObject.AddComponent<StageEngine>();
			this.gameObject.AddComponent<UIContentScaler>();
			this.gameObject.SetActive(true);
			Object.DontDestroyOnLoad(this.gameObject);

			this.cachedTransform.localScale = new Vector3(StageCamera.UnitsPerPixel, StageCamera.UnitsPerPixel, StageCamera.UnitsPerPixel);

			EnableSound();

			Timers.inst.Add(5, 0, RunTextureCollector);

#if UNITY_5_4_OR_NEWER
			SceneManager.sceneLoaded += SceneManager_sceneLoaded;
#endif
			_focusRemovedDelegate = OnFocusRemoved;
		}
```

通过UnityEngine提供的Object.DontDestroyOnLoad方法，将Stage物件设置为不在加载新场景时销毁。

除此之外，使用unity提供了UnityEngine.SceneManagement命名空间下SceneManager.sceneLoaded这个事件，在任一UnityEngine.SceneManagement.Scene场景加载后，执行StageCamera.CheckMainCamera()方法，来确认fairy主相机的存在。

### StageEngine

在Stage构造时，给它挂上了一个StageEngine组件。

StageEngine组件可以展示，所有FairyGUI物件的活动状态信息，即FairyGUI.Stats类中记录的静态值。

#### 每帧更新

StageEngine继承自UnityEngine.MonoBehaviour，因而可执行unity开放的多种接口。

![StageEngine](/image-20191107163309097.png)

所有的更新方法，都放在unity提供的LateUpdate中执行。

```c#
		void LateUpdate()
		{
			Stage.inst.InternalUpdate();

			ObjectsOnStage = Stats.ObjectCount;
			GraphicsOnStage = Stats.GraphicsCount;
		}
```

因而执行了Stage.InternalUpdate()方法。

```c#
		internal void InternalUpdate()
		{
			HandleEvents();

			_updateContext.Begin();
			Update(_updateContext);
			_updateContext.End();

			if (DynamicFont.textRebuildFlag)
			{
				//字体贴图更改了，重新渲染一遍，防止本帧文字显示错误
				_updateContext.Begin();
				Update(_updateContext);
				_updateContext.End();

				DynamicFont.textRebuildFlag = false;
			}
		}
```

因而执行了Container.Update()方法，执行了Container的基类DisplayObject的Update()方法，以及此Container的所有子节点DisplayObject的Update()方法。

```c#
		override public void Update(UpdateContext context)
		{
			if (_isPanel && !gameObject.activeInHierarchy)
				return;

			base.Update(context);

			if (_cacheAsBitmap && _paintingMode != 0 && _paintingFlag == 2)
			{
				if (onUpdate != null)
					onUpdate();
				return;
			}

			if (_mask != null)
			{
				context.EnterClipping(this.id, reversedMask);
				_mask.graphics._PreUpdateMask(context);
			}
			else if (_clipRect != null)
				context.EnterClipping(this.id, this.TransformRect((Rect)_clipRect, null), clipSoftness);

			float savedAlpha = context.alpha;
			context.alpha *= this.alpha;
			bool savedGrayed = context.grayed;
			context.grayed = context.grayed || this.grayed;

			if (_fBatching)
				context.batchingDepth++;

			if (context.batchingDepth > 0)
			{
				int cnt = _children.Count;
				for (int i = 0; i < cnt; i++)
				{
					DisplayObject child = _children[i];
					if (child.visible)
						child.Update(context);
				}
			}
			else
			{
				if (_mask != null)
					_mask.renderingOrder = context.renderingOrder++;

				int cnt = _children.Count;
				for (int i = 0; i < cnt; i++)
				{
					DisplayObject child = _children[i];
					if (child.visible)
					{
						if (child != _mask)
							child.renderingOrder = context.renderingOrder++;

						child.Update(context);
					}
				}

				if (_mask != null)
					_mask.graphics._SetStencilEraserOrder(context.renderingOrder++);
			}

			if (_fBatching)
			{
				if (context.batchingDepth == 1)
					SetRenderingOrder(context);
				context.batchingDepth--;
			}

			context.alpha = savedAlpha;
			context.grayed = savedGrayed;

			if (_clipRect != null || _mask != null)
				context.LeaveClipping();

			if (_paintingMode > 0 && paintingGraphics.texture != null)
				UpdateContext.OnEnd += _captureDelegate;

			if (onUpdate != null)
				onUpdate();
		}
```

### UIContentScaler

一般都需要将这个组件，手动挂到unity场景中，或者在业务层代码中自行添加，来设置适配模式。

![UIContentScaler](/image-20191028145239101.png)

相关编辑器扩展的源码，在FairyGUIEditor.UIContentScalerEditor。





## fairy包

### UIPackage概览

UIPackage的全部内容：

1. ##### 管理所有已加载的fairy包

   | 字段/属性/方法                                               | 用途                                                         |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| static List\<UIPackage\> _packageList<br/>static Dictionary<string, UIPackage> _packageInstById<br/>static Dictionary<string, UIPackage> _packageInstByName | 运行时所有已加载fairy包                                      |
| internal static int _constructing                            | 记录正在构造中的fairy元件的数量                              |
| public static UIPackage GetById(string id)<br/>public static UIPackage GetByName(string name)<br/>public static List\<UIPackage> GetPackages() | 获取已加载的fairy包                                          |
| public static UIPackage AddPackage(AssetBundle bundle)<br/>public static UIPackage AddPackage(AssetBundle desc, AssetBundle res)<br/>public static UIPackage AddPackage(AssetBundle desc, AssetBundle res, string mainAssetName)<br/>public static UIPackage AddPackage(string descFilePath)<br/>public static UIPackage AddPackage(string assetPath, LoadResource loadFunc)<br/>public static UIPackage AddPackage(byte[] descData, string assetNamePrefix, LoadResource loadFunc) | 加载fairy包                                                  |
  | public static void RemovePackage(string packageIdOrName)<br/>public static void RemoveAllPackages() | 卸载fairy包                                                  |
   | public static GObject CreateObject(string pkgName, string resName)<br/>public static GObject CreateObject(string pkgName, string resName, System.Type userClass)<br/>public static GObject CreateObjectFromURL(string url)<br/>public static GObject CreateObjectFromURL(string url, System.Type userClass)<br/>public static void CreateObjectAsync(string pkgName, string resName, CreateObjectCallback callback)<br/>public static void CreateObjectFromURL(string url, CreateObjectCallback callback) | 创建指定包内的指定项目                                       |
   | public static object GetItemAsset(string pkgName, string resName)<br/>public static object GetItemAssetByURL(string url)<br/>public static PackageItem GetItemByURL(string url)<br/>static int ComparePackageItem(PackageItem p1, PackageItem p2) | 获取指定包内的指定项目                                       |
   | public static string GetItemURL(string pkgName, string resName)<br/>public static string NormalizeURL(string url) | 包内资源的路径字符串形式转换                                 |
   | public static void SetStringsSource(XML source)              | 加载XML格式的动效文件<html><font color='red'>（无引用）</font></html> |


2. ##### 对应一个fairy包

   | 字段/属性/方法                                               | 用途                       |
   | ------------------------------------------------------------ | -------------------------- |
   | public string id                                             | 此包的唯一ID               |
   | public string name                                           | 包名                       |
   | public string assetPath                                      | 此包的资源路径             |
   | List\<PackageItem\> _items<br/>Dictionary<string, PackageItem> _itemsByName<br/>Dictionary<string, PackageItem> _itemsByName | 此包的所有包内项目         |
   | Dictionary<string, string>[] _dependencies<br/>public Dictionary<string, string>[] dependencies | 此包的所有依赖项           |
   | AssetBundle _resBundle<br/>public AssetBundle resBundle<br/>bool _fromBundle | 此包的ab资源               |
   | string _customId<br/>public string customId                  | 自定义替换id值             |
   | LoadResource _loadFun                                        | 加载此包后的回调委托       |
   | Dictionary<string, AtlasSprite> _sprites                     | 此包所涉及的所有图集资源   |
   | public UIPackage()                                           | 此包的构造函数             |
   | bool LoadPackage(ByteBuffer buffer, string packageSource, string assetNamePrefix) | 加载此包                   |
   | public void LoadAllAssets()<br/>public void ReloadAssets()<br/>public void ReloadAssets(AssetBundle resBundle)<br/>void LoadAtlas(PackageItem item)<br/>void LoadImage(PackageItem item)<br/>void LoadSound(PackageItem item)<br/>byte[] LoadBinary(PackageItem item)<br/>void LoadMovieClip(PackageItem item)<br/>void LoadFont(PackageItem item) | 加载此包内的项目数据和资源 |
   | public void UnloadAssets()                                   | 卸载此包的数据             |
   | void Dispose()                                               | 销毁此包                   |
   | public GObject CreateObject(string resName)<br/>public GObject CreateObject(string resName, System.Type userClass)<br/>public void CreateObjectAsync(string resName, CreateObjectCallback callback)<br/>GObject CreateObject(PackageItem item, System.Type userClass) | 创建此包内的项目           |
   | public object GetItemAsset(string resName)<br/>public List\<PackageItem> GetItems()<br/>public PackageItem GetItem(string itemId)<br/>public PackageItem GetItemByName(string itemName)<br/>public object GetItemAsset(PackageItem item) | 获取此包内的项目           |

3. ##### 内嵌内容

   | 类型         | 内嵌内容                                                     | 描述                      |
   | ------------ | ------------------------------------------------------------ | ------------------------- |
   | 公开静态常量 | public const string URL_PREFIX                               | 包内资源路径字符串的前缀  |
   | 委托         | public delegate object LoadResource(string name, string extension, System.Type type, out DestroyMethod destroyMethod); | fairy包加载完成后的回调   |
   | 委托         | public delegate void CreateObjectCallback(GObject result);   | fairy元件创建完成后的回调 |
   | 内嵌私有类   | class AtlasSprite                                            | 图集                      |

### 加载fairy包

使用全局的UIPackage.AddPackage()方法，可以加载整个fairy包内的所有项目。

在全局的UIPackage.AddPackage()的多种重载方法中，加载了此fairy包的主数据文件，并解析；

然后，创建了一个UIPackage类的对象，调用此对象私有的LoadPackage()方法，遍历主数据文件的内容，加载其中所有涉及到的资源。

#### 加载主数据文件

对于全局的UIPackage.AddPackage()方法，fairy提供了多种传参类型，根据传参类型可以将这些方法分为以下3类。

1. 使用UnityEngine.AssetBundle包
2. 直接使用fairy包名
3. 直接使用二进制数据

##### 使用UnityEngine.AssetBundle包

fairy所导出的所有文件，被打成一个AssetBundle包，作为desc参数，传进来。

此fairy包所使用的外部资源文件，被导出一个AssetBundle包，作为res参数，传进来。如果这个参数被缺省，则使用desc；如果这个参数不同于desc，则只保留desc的主数据内容，而弃用desc。

mainAssetName为主数据的文件名。如果缺省，则遍历所有desc内容，去查找到它。

```c#
		public static UIPackage AddPackage(AssetBundle desc, AssetBundle res, string mainAssetName)
		{
			byte[] source = null;
#if (UNITY_5 || UNITY_5_3_OR_NEWER)
			if (mainAssetName != null)
			{
				TextAsset ta = desc.LoadAsset<TextAsset>(mainAssetName);
				if (ta != null)
					source = ta.bytes;
			}
			else
			{
				string[] names = desc.GetAllAssetNames();
				string searchPattern = "_fui";
				foreach (string n in names)
				{
					if (n.IndexOf(searchPattern) != -1)
					{
						TextAsset ta = desc.LoadAsset<TextAsset>(n);
						if (ta != null)
						{
							source = ta.bytes;
							mainAssetName = Path.GetFileNameWithoutExtension(n);
							break;
						}
					}
				}
			}
#else
			if (mainAssetName != null)
			{
				TextAsset ta = (TextAsset)desc.Load(mainAssetName, typeof(TextAsset));
				if (ta != null)
					source = ta.bytes;
			}
			else
			{
				source = ((TextAsset)desc.mainAsset).bytes;
				mainAssetName = desc.mainAsset.name;
			}
#endif
			if (source == null)
				throw new Exception("FairyGUI: no package found in this bundle.");

			if (desc != res)
				desc.Unload(true);

			ByteBuffer buffer = new ByteBuffer(source);

			UIPackage pkg = new UIPackage();
			pkg._resBundle = res;
			pkg._fromBundle = true;
			int pos = mainAssetName.IndexOf("_fui");
			string assetNamePrefix;
			if (pos != -1)
				assetNamePrefix = mainAssetName.Substring(0, pos);
			else
				assetNamePrefix = mainAssetName;
			if (!pkg.LoadPackage(buffer, res.name, assetNamePrefix))
				return null;

			_packageInstById[pkg.id] = pkg;
			_packageInstByName[pkg.name] = pkg;
			_packageList.Add(pkg);

			return pkg;
		}
```

将desc这个AssetBundle文件解压后，就得到了fairy的所有导出文件。

fairy的导出文件，包含一个名为`包名_fui.bytes`的二进制文件（主数据），和多个资源文件（某些资源文件也可能为bytes类型）。

这个主数据文件，为解析fairy包的入口，作为mainAssetName参数传入；如果没有传入此参数，将遍历所有的AssetBundle解压文件（即fairy导出文件），直到找到包含`_fui`字符串的那个文件，记录下它的名称。

使用UnityEngine的AssetBundle.LoadAsset\<TextAsset>()方法，来解析这个主数据bytes文件，得到了它的UnityEngine.TextAsset数据。

根据它的数据内容（[byte[]] TextAsset.bytes），能创建一个ByteBuffer类的对象。

如果desc这个AssetBundle不同于res，则把desc整个AssetBundle包全部卸载掉。（但能留下desc的主数据内容，被记录在了ByteBuffer类的对象中。）

根据res这个AssetBundle，创建一个新的UIPackage类的对象。

然后使用这个UIPackage对象的LoadPackage()方法加载此包。这里传入的参数依次为：以desc主数据文件为数据创建的ByteBuffer类的对象，res的文件名，desc中的包名。

最后将此包记录在此管理类的已加载包列表字段中。

##### 直接使用fairy包名

可以直接传入此fairy包的包名（包含了相对路径），来加载fairy包。

```c#
		public static UIPackage AddPackage(string descFilePath)
		{
			if (descFilePath.StartsWith("Assets/"))
			{
#if UNITY_EDITOR
				return AddPackage(descFilePath, (string name, string extension, System.Type type, out DestroyMethod destroyMethod) =>
				{
					destroyMethod = DestroyMethod.Unload;
					return AssetDatabase.LoadAssetAtPath(name + extension, type);
				});
#else
				
				Debug.LogWarning("FairyGUI: failed to load package in '" + descFilePath + "'");
				return null;
#endif
			}
			return AddPackage(descFilePath, (string name, string extension, System.Type type, out DestroyMethod destroyMethod) =>
			{
				destroyMethod = DestroyMethod.Unload;
				return Resources.Load(name, type);
			});
		}

		public static UIPackage AddPackage(string assetPath, LoadResource loadFunc)
		{
			if (_packageInstById.ContainsKey(assetPath))
				return _packageInstById[assetPath];

			DestroyMethod dm;
			TextAsset asset = (TextAsset)loadFunc(assetPath + "_fui", ".bytes", typeof(TextAsset), out dm);
			if (asset == null)
			{
				if (Application.isPlaying)
					throw new Exception("FairyGUI: Cannot load ui package in '" + assetPath + "'");
				else
					Debug.LogWarning("FairyGUI: Cannot load ui package in '" + assetPath + "'");
			}

			ByteBuffer buffer = new ByteBuffer(asset.bytes);

			UIPackage pkg = new UIPackage();
			pkg._loadFunc = loadFunc;
			pkg.assetPath = assetPath;
			if (!pkg.LoadPackage(buffer, assetPath, assetPath))
				return null;

			_packageInstById[pkg.id] = pkg;
			_packageInstByName[pkg.name] = pkg;
			_packageInstById[assetPath] = pkg;
			_packageList.Add(pkg);
			return pkg;
		}
```

根据fairy包名，可找到此fairy包的主数据文件。

使用传入的LoadResource委托loadFunc参数，来解析这个主数据文件；如果此参数被缺省，则默认使用UnityEditor的AssetDatabase.LoadAssetAtPath()静态方法，来解析此bytes文件。

将解析结果（object类型），强制转换为UnityEngine.TextAsset类型。

一如既往。根据此TextAsset数据的内容，创建一个ByteBuffer类的对象。

根据包名，创建一个新的UIPackage类的对象。

然后使用这个UIPackage对象的LoadPackage()方法加载此包。这里传入的参数依次为：以此包的主数据文件为数据创建的ByteBuffer类的对象，包名，包名。

最后将此包记录在此管理类的已加载包列表字段中。

##### 直接使用二进制数据

可以直接传入二进制数据，将其加载为fairy包的形式。

```c#
		public static UIPackage AddPackage(byte[] descData, string assetNamePrefix, LoadResource loadFunc)
		{
			ByteBuffer buffer = new ByteBuffer(descData);

			UIPackage pkg = new UIPackage();
			pkg._loadFunc = loadFunc;
			if (!pkg.LoadPackage(buffer, "raw data", assetNamePrefix))
				return null;

			_packageInstById[pkg.id] = pkg;
			_packageInstByName[pkg.name] = pkg;
			_packageList.Add(pkg);

			return pkg;
		}
```

根据传入的二进制数据，创建一个ByteBuffer类的对象。

创建一个新的UIPackage类的对象。

使用这个UIPackage对象的LoadPackage()方法加载此包。这里传入的参数依次为：以传入二进制数据为数据创建的ByteBuffer类的对象，统一字符`raw data`，传入的前缀名。

将此包记录在此管理类的已加载包列表字段中。

#### 载入所涉及的资源文件

```c#
		bool LoadPackage(ByteBuffer buffer, string packageSource, string assetNamePrefix)
		{
			if (buffer.ReadUint() != 0x46475549)
			{
				if (Application.isPlaying)
					throw new Exception("FairyGUI: old package format found in '" + packageSource + "'");
				else
				{
					Debug.LogWarning("FairyGUI: old package format found in '" + packageSource + "'");
					return false;
				}
			}

			buffer.version = buffer.ReadInt();
			buffer.ReadBool(); //compressed
			id = buffer.ReadString();
			name = buffer.ReadString();
			if (_packageInstById.ContainsKey(id) && name != _packageInstById[id].name)
			{
				Debug.LogWarning("FairyGUI: Package id conflicts, '" + name + "' and '" + _packageInstById[id].name + "'");
				return false;
			}
			buffer.Skip(20);
			int indexTablePos = buffer.position;
			int cnt;

			buffer.Seek(indexTablePos, 4);

			cnt = buffer.ReadInt();
			string[] stringTable = new string[cnt];
			for (int i = 0; i < cnt; i++)
				stringTable[i] = buffer.ReadString();
			buffer.stringTable = stringTable;

			if (buffer.Seek(indexTablePos, 5))
			{
				cnt = buffer.ReadInt();
				for (int i = 0; i < cnt; i++)
				{
					int index = buffer.ReadUshort();
					int len = buffer.ReadInt();
					stringTable[index] = buffer.ReadString(len);
				}
			}

			buffer.Seek(indexTablePos, 1);

			PackageItem pi;

			if (assetNamePrefix == null)
				assetNamePrefix = string.Empty;
			else if (assetNamePrefix.Length > 0)
				assetNamePrefix = assetNamePrefix + "_";

			cnt = buffer.ReadShort();
			for (int i = 0; i < cnt; i++)
			{
				int nextPos = buffer.ReadInt();
				nextPos += buffer.position;

				pi = new PackageItem();
				pi.owner = this;
				pi.type = (PackageItemType)buffer.ReadByte();
				pi.id = buffer.ReadS();
				pi.name = buffer.ReadS();
				buffer.ReadS(); //path
				pi.file = buffer.ReadS();
				pi.exported = buffer.ReadBool();
				pi.width = buffer.ReadInt();
				pi.height = buffer.ReadInt();

				switch (pi.type)
				{
					case PackageItemType.Image:
						{
							pi.objectType = ObjectType.Image;
							int scaleOption = buffer.ReadByte();
							if (scaleOption == 1)
							{
								Rect rect = new Rect();
								rect.x = buffer.ReadInt();
								rect.y = buffer.ReadInt();
								rect.width = buffer.ReadInt();
								rect.height = buffer.ReadInt();
								pi.scale9Grid = rect;

								pi.tileGridIndice = buffer.ReadInt();
							}
							else if (scaleOption == 2)
								pi.scaleByTile = true;

							buffer.ReadBool(); //smoothing
							break;
						}

					case PackageItemType.MovieClip:
						{
							buffer.ReadBool(); //smoothing
							pi.objectType = ObjectType.MovieClip;
							pi.rawData = buffer.ReadBuffer();
							break;
						}

					case PackageItemType.Font:
						{
							pi.rawData = buffer.ReadBuffer();
							break;
						}

					case PackageItemType.Component:
						{
							int extension = buffer.ReadByte();
							if (extension > 0)
								pi.objectType = (ObjectType)extension;
							else
								pi.objectType = ObjectType.Component;
							pi.rawData = buffer.ReadBuffer();

							UIObjectFactory.ResolvePackageItemExtension(pi);
							break;
						}

					case PackageItemType.Atlas:
					case PackageItemType.Sound:
					case PackageItemType.Misc:
						{
							pi.file = assetNamePrefix + pi.file;
							break;
						}
				}
				_items.Add(pi);
				_itemsById[pi.id] = pi;
				if (pi.name != null)
					_itemsByName[pi.name] = pi;

				buffer.position = nextPos;
			}

			buffer.Seek(indexTablePos, 2);

			cnt = buffer.ReadShort();
			for (int i = 0; i < cnt; i++)
			{
				int nextPos = buffer.ReadShort();
				nextPos += buffer.position;

				string itemId = buffer.ReadS();
				pi = _itemsById[buffer.ReadS()];

				AtlasSprite sprite = new AtlasSprite();
				sprite.atlas = pi;
				sprite.rect.x = buffer.ReadInt();
				sprite.rect.y = buffer.ReadInt();
				sprite.rect.width = buffer.ReadInt();
				sprite.rect.height = buffer.ReadInt();
				sprite.rotated = buffer.ReadBool();
				_sprites[itemId] = sprite;

				buffer.position = nextPos;
			}

			if (buffer.Seek(indexTablePos, 3))
			{
				cnt = buffer.ReadShort();
				for (int i = 0; i < cnt; i++)
				{
					int nextPos = buffer.ReadInt();
					nextPos += buffer.position;

					if (_itemsById.TryGetValue(buffer.ReadS(), out pi))
					{
						if (pi.type == PackageItemType.Image)
						{
							pi.pixelHitTestData = new PixelHitTestData();
							pi.pixelHitTestData.Load(buffer);
						}
					}

					buffer.position = nextPos;
				}
			}

			if (!Application.isPlaying)
				_items.Sort(ComparePackageItem);

			buffer.Seek(indexTablePos, 0);
			cnt = buffer.ReadShort();
			_dependencies = new Dictionary<string, string>[cnt];
			for (int i = 0; i < cnt; i++)
			{
				Dictionary<string, string> kv = new Dictionary<string, string>();
				kv.Add("id", buffer.ReadS());
				kv.Add("name", buffer.ReadS());
				_dependencies[i] = kv;
			}

			return true;
		}
```

解析传入的ByteBuffer数据，按类型创建所有包内项目。

### ByteBuffer

#### 概览

FairyGUI.Utils.ByteBuffer用于解析fairy包的主数据二进制文件。

![PackageItem](/image-20191104100340406.png)

公开的position属性和私有的_pointer字段一致，为记录当前解析位置的int值。

每解析几个byte字节，就将当前解析位置移动几个字节，下次再从当前位置开始解析。

使用多种不同的Read()方法，从当前解析字节位置开始，在要求类型的字节长度内，将这些byte字节解析为所要求类型的数据。

使用Skip()方法，可以跳过几个byte字节，不解析，而只移动当前解析位置。

使用Seek()方法，可以根据指定索引的byte值，跳过几个字节。

#### 解析字符串

解析字符串有ReadString()和ReadS()两种方法。

加载fairy包时，第一次解析，找出其中所有的字符串，使用ReadString()，存入了[string[]]stringTable字段中；

之后需要解析字符串时，可以使用ReadS()方法，直接从此数组中取值，读取当前解析字节位置开始的字符串。

需要修改字符串内容时，使用WriteS()方法，将新的数据直接修改存入stringTable字段中，之后即可使用ReadS()方法读取到新数据。

#### ZipReader

ByteBuffer.littleEndian字段记录了_data数据是否来自zip文件。

如果不是来自zip文件，则解析字节时，需将数据倒序处理；

如果来自未解压的zip文件，则解析字节时无需倒序处理（目前无引用）。

### PackageItem

一个PackageItem对象就是一个包内项目。

![PackageItem](/image-20191104100255757.png)

#### type和objectType

PackageItem的type字段和objectType字段的比较。

|                       type                        |                       objectType                        |
| :-----------------------------------------------: | :-----------------------------------------------------: |
| ![PackageItem.type](/image-20191101190720899.png) | ![PackageItem.objectType](/image-20191101190746365.png) |
| ![PackageItemType](/image-20191101190955691.png)  |       ![ObjectType](/image-20191101191058631.png)       |

这两个字段都是在UIPackage类的对象的LoadPackage()方法执行时被赋值。

type字段为解析ByteBuffer数据直接得到的值。

objectType字段是在type字段被赋值后，根据其值的不同，而在其分支中被赋值；

它可能为空值，所以不能作为分类依据，而只能作为一个标识。

#### 包内项目不等同于fairy组件

一个包内项目PackageItem，并不等同于一个元件。

它跟fairy数据存储规则相关。它的数据来自于ByteBuffer的解析结果。

一个元件可能会被解析为多个包内项目。比如，一个图片元件，它会被解析为，一个type为Image的PackageItem，和一个type为Atlas（不重复）的PackageItem。

如果一个fairy组件，在fairy编辑器中没有被设置为导出，且没有设置为导出的组件引用它，那么解析结果中，将不包含此组件的相关信息。

### 创建fairy元件

在包加载完成后，可以创建fairy元件。

如果fairy包没有加载，则会报错提示。

创建fairy元件的方法很多，按它们最终执行的方法，分为两类：

1. 同步创建
2. 异步创建

#### 同步创建

所有同步创建fairy元件的方法，最终都需调用下面这个UIPackage类的对象的CreateObject()方法。

```c#
		GObject CreateObject(PackageItem item, System.Type userClass)
		{
			Stats.LatestObjectCreation = 0;
			Stats.LatestGraphicsCreation = 0;

			GetItemAsset(item);

			GObject g = null;
			if (item.type == PackageItemType.Component)
			{
				if (userClass != null)
					g = (GComponent)Activator.CreateInstance(userClass);
				else
					g = UIObjectFactory.NewObject(item);
			}
			else
				g = UIObjectFactory.NewObject(item);

			if (g == null)
				return null;

			_constructing++;
			g.packageItem = item;
			g.ConstructFromResource();
			_constructing--;
			return g;
		}
```

根据包数据中记录的此项目的不同类型，把它创建出来，然后执行它的构造函数。

创建方法有两大类：

1. 自定义类型

   这里，允许扩展fairy内置的PackageItemType枚举类型；

   但此扩展类型必须继承自FairyGUI.GComponent；

   将真实的类型，作为userClass参数传入；

   调用System.Activator.CreateInstance()静态方法；

   并将得到的object对象，强制转换为GComponent类型。

2. fairy自带的类型

   对于fairy自带类型，调用FairyGUI.UIObjectFactory.NewObject()静态方法；

   如果有自定义的PackageItem.extensionCreator()方法，则执行它；

   默认则根据此PackageItem对象objectType的不同，而执行各组件类的构造函数。

#### 异步创建

所有异步创建fairy元件的方法，最终都调用了AsyncCreationHelper.CreateObject()方法。

```c#
		public static void CreateObject(PackageItem item, UIPackage.CreateObjectCallback callback)
		{
			Timers.inst.StartCoroutine(_CreateObject(item, callback));
		}

		static IEnumerator _CreateObject(PackageItem item, UIPackage.CreateObjectCallback callback)
		{
			Stats.LatestObjectCreation = 0;
			Stats.LatestGraphicsCreation = 0;

			float frameTime = UIConfig.frameTimeForAsyncUIConstruction;

			List<DisplayListItem> itemList = new List<DisplayListItem>();
			DisplayListItem di = new DisplayListItem(item, ObjectType.Component);
			di.childCount = CollectComponentChildren(item, itemList);
			itemList.Add(di);

			int cnt = itemList.Count;
			List<GObject> objectPool = new List<GObject>(cnt);
			GObject obj;
			float t = Time.realtimeSinceStartup;
			bool alreadyNextFrame = false;

			for (int i = 0; i < cnt; i++)
			{
				di = itemList[i];
				if (di.packageItem != null)
				{
					obj = UIObjectFactory.NewObject(di.packageItem);
					obj.packageItem = di.packageItem;
					objectPool.Add(obj);

					UIPackage._constructing++;
					if (di.packageItem.type == PackageItemType.Component)
					{
						int poolStart = objectPool.Count - di.childCount - 1;

						((GComponent)obj).ConstructFromResource(objectPool, poolStart);

						objectPool.RemoveRange(poolStart, di.childCount);
					}
					else
					{
						obj.ConstructFromResource();
					}
					UIPackage._constructing--;
				}
				else
				{
					obj = UIObjectFactory.NewObject(di.type);
					objectPool.Add(obj);

					if (di.type == ObjectType.List && di.listItemCount > 0)
					{
						int poolStart = objectPool.Count - di.listItemCount - 1;
						for (int k = 0; k < di.listItemCount; k++)
							((GList)obj).itemPool.ReturnObject(objectPool[k + poolStart]);
						objectPool.RemoveRange(poolStart, di.listItemCount);
					}
				}

				if ((i % 5 == 0) && Time.realtimeSinceStartup - t >= frameTime)
				{
					yield return null;
					t = Time.realtimeSinceStartup;
					alreadyNextFrame = true;
				}
			}

			if (!alreadyNextFrame)
				yield return null;

			callback(objectPool[0]);
		}
```

创建一个列表，用来记录这个组件的所有显示内容(DisplayListItem)。

首先，把这个PackageItem本身，作为一个objectType为ObjectType.Component的显示内容放入列表。

然后，把其各层子节点全部放入这个列表。

对应这个DisplayListItem列表，创建一个等大的GObject的对象池。

创建新的GObject，并放入对象池中。

执行此GObject对象的构造函数。

创建5个之后，等待下一帧再继续执行。

在下帧执行的时候，才执行创建后的回调。




## fairy元件与unity物件的关联

### 创建UnityEngine.GameObject

#### FairyGUI.DisplayObject创建UnityEngine.GameObject

FairyGUI.DisplayObject通过其CreateGameObject等方法来创建UnityEngine.GameObject，并将这个物件放置到unity的DontDestroyOnLoad场景。

```c#
		protected void CreateGameObject(string gameObjectName)
		{
			gameObject = new GameObject(gameObjectName);
			cachedTransform = gameObject.transform;
			if (Application.isPlaying)
				Object.DontDestroyOnLoad(gameObject);
			gameObject.hideFlags = DisplayOptions.hideFlags;
			gameObject.SetActive(false);

#if FAIRYGUI_TEST
			DisplayObjectInfo info = gameObject.AddComponent<DisplayObjectInfo>();
			info.displayObject = this;
#endif

			_ownsGameObject = true;
		}
```

之后，对于FairyGUI.DisplayObject，可以通过其gameObject属性来访问到UnityEngine.GameObject。

![DisplayObject.gameObject](/image-20191025195401682.png)

#### FairyGUI.GObject创建UnityEngine.GameObject

FairyGUI.GObject中有个CreateDisplayObject虚方法，由它的子类去复写这个虚方法，根据子类不同的需求去创建FairyGUI.DisplayObject，从而创建UnityEngine.GameObject。

![override GObject.CreateDisplayObject](/image-20191026113449931.png)

以FairyGUI.GComponent为例，它创建了一个FairyGUI.Container（继承自FairyGUI.DisplayObject）。

```c#
		override protected void CreateDisplayObject()
		{
			rootContainer = new Container("GComponent");
			rootContainer.gOwner = this;
			rootContainer.onUpdate = OnUpdate;
			container = rootContainer;

			displayObject = rootContainer;
		}
```

之后，对于FairyGUI.GObject，可以通过其displayObject属性来访问FairyGUI.DisplayObject，从而访问到UnityEngine.GameObject。

![GObject.displayObject](/image-20191025200048283.png)



#### 在Unity3D编辑器中查看FairyGUI创建的物件的信息

当**FAIRYGUI_TEST**这个fairy自定义给unity的宏开启后，FairyGUI.DisplayObject在创建UnityEngine.GameObject时，为其添加了**DisplayObjectInfo**组件。

fairy在其Editor目录下，**DisplayObjectEditor**为DisplayObjectInfo组件定制了其unity编辑器扩展内容。

```c#
	[CustomEditor(typeof(DisplayObjectInfo))]
	public class DisplayObjectEditor : Editor
```

在Unity3D编辑器运行时，可以在Inspector视窗中查看此UnityEngine.GameObject所对应的FairyGUI.DisplayObject相关信息。

![DisplayObjectEditor](/image-20191026144518747.png)

### fairy创建物件汇总

#### 显示物件的分类

以上得出，所有的UnityEngine.GameObject都由FairyGUI.DisplayObject来创建。

在类图中发现，DisplayObject的子类，分为3大类：

- 空物件Container
- 平面UI物件，包括：
  - 图片Image
  - 文本TextField
  - 图形Shape
  - 选项图形SelectionShape
- 3D物件GoWrapper

### NGraphics

#### MeshFilter和MeshRenderer

这些平面物件类型，在创建时，均创建了一个NGraphics类的对象。

```c#
		public NGraphics(GameObject gameObject)
		{
			this.gameObject = gameObject;

			_alpha = 1f;
			_shader = ShaderConfig.imageShader;
			_color = Color.white;
			_meshFactory = this;

			meshFilter = gameObject.AddComponent<MeshFilter>();
			meshRenderer = gameObject.AddComponent<MeshRenderer>();
#if (UNITY_5 || UNITY_5_3_OR_NEWER)
			meshRenderer.shadowCastingMode = UnityEngine.Rendering.ShadowCastingMode.Off;
			meshRenderer.reflectionProbeUsage = UnityEngine.Rendering.ReflectionProbeUsage.Off;
#else
			meshRenderer.castShadows = false;
#endif
			meshRenderer.receiveShadows = false;

			mesh = new Mesh();
			mesh.name = gameObject.name;
			mesh.MarkDynamic();

			meshFilter.mesh = mesh;

			meshFilter.hideFlags = DisplayOptions.hideFlags;
			meshRenderer.hideFlags = DisplayOptions.hideFlags;
			mesh.hideFlags = DisplayOptions.hideFlags;

			Stats.LatestGraphicsCreation++;
		}
```

FairyGUI.NGraphics在构建时，

为这个UnityEngine.GameObject创建了，

一个UnityEngine.MeshFilter，和，一个UnityEngine.MeshRenderer组件，

并将MeshFilter组件的mesh作为其mesh属性存储下来。

#### Material

NGraphics的，material属性，和，_material字段，为UnityEngine.Material类型，

存储了于这个NGraphics相关的MeshRenderer.sharedMaterial的材质球信息。

```c#
		public Material material
		{
			get { return _material; }
			set
			{
				_material = value;
				if (_material != null)
				{
					_customMatarial = true;
					meshRenderer.sharedMaterial = _material;
					if (_texture != null)
						_material.mainTexture = _texture.nativeTexture;
				}
				else
				{
					_customMatarial = false;
					meshRenderer.sharedMaterial = null;
				}
			}
		}
```

#### 更改着色器和贴图

##### 1.NGraphics.UpdateManager()

NGraphics中的UpdateManager()方法，用来对着色器和纹理贴图，做统一更新处理。

```c#
		void UpdateManager()
		{
			MaterialManager mm;
			if (_texture != null)
				mm = _texture.GetMaterialManager(_shader, _materialKeywords);
			else
				mm = null;
			if (_manager != null && _manager != mm)
				_manager.Release();
			_manager = mm;
		}
```

这里，创建了一个FairyGUI.MaterialManager类的对象，并将它存储在了NGraphics._manager字段中。

##### 2.创建MaterialManager

通过NTexture.GetMaterialManager()方法来创建MaterialManager。

```c#
		public MaterialManager GetMaterialManager(string shaderName, string[] keywords)
		{
			if (_root != this)
			{
				if (_root == null)
					return null;
				else
					return _root.GetMaterialManager(shaderName, keywords);
			}

			if (_materialManagers == null)
				_materialManagers = new Dictionary<string, MaterialManager>();

			string key = shaderName;
			if (keywords != null)
			{
				//对于带指定关键字的，目前的设计是不参加共享材质了，因为逻辑会变得更复杂
				key = shaderName + "_" + _gCounter++;
			}

			MaterialManager mm;
			if (!_materialManagers.TryGetValue(key, out mm))
			{
				mm = new MaterialManager(this, ShaderConfig.GetShader(shaderName), keywords);
				mm._managerKey = key;
				_materialManagers.Add(key, mm);
			}

			return mm;
		}
```

##### 3.获取着色器

直接使用UnityEngine提供的Shader.Find()方法来获取着色器UnityEngine.Shader。

```c#
		public static Shader GetShader(string name)
		{
			Shader shader = Get(name);
			if (shader == null)
			{
				Debug.LogWarning("FairyGUI: shader not found: " + name);
				shader = Shader.Find("UI/Default");
			}
			shader.hideFlags = DisplayOptions.hideFlags;

			if (_properyIDs == null)
				InitPropertyIDs();

			return shader;
		}
```

#### 每帧更新

上文StageEngine部分提到，在StageEngine这个继承自UnityEngine.MonoBehaviour的类中，有LateUpdate()方法，调用了根目录下所有DisplayObject子节点的Update方法。

在DisplayObject.Update()方法中，调用了NGraphics.Update()方法。

（待定：渲染逻辑）

### Image

#### 纹理贴图的数据流

##### 1.在构建GImage时，设置Image内容

Image在GImage中，作为其DisplayObject.displayObject属性和GImage._content字段而被存储。

在此GImage类的对象，被构建时，执行了其ConstructFromResource()方法。

```c#
		override public void ConstructFromResource()
		{
			packageItem.Load();

			sourceWidth = packageItem.width;
			sourceHeight = packageItem.height;
			initWidth = sourceWidth;
			initHeight = sourceHeight;
			_content.scale9Grid = packageItem.scale9Grid;
			_content.scaleByTile = packageItem.scaleByTile;
			_content.tileGridIndice = packageItem.tileGridIndice;
			_content.texture = packageItem.texture;

			SetSize(sourceWidth, sourceHeight);
		}
```

##### 2.加载图片LoadImage()

此方法中，首先调用了PackageItem的Load()方法，而最终调用了UIPackage类的对象的GetItemAsset()方法。

由于其type值为PackageItemType.Image，所以，执行了LoadImage()方法。

```c#
		void LoadImage(PackageItem item)
		{
			AtlasSprite sprite;
			if (_sprites.TryGetValue(item.id, out sprite))
				item.texture = new NTexture((NTexture)GetItemAsset(sprite.atlas), sprite.rect, sprite.rotated);
			else
				item.texture = NTexture.Empty;
		}
```

##### 3.加载图集LoadAtlas()

根据此图片PackageItem，在UIPackage记录的_sprites词典中，找到对应的AtlasSprite图集数据。

也就找到了此图片PackageItem，所对应的图集PackageItem。

再次调用UIPackage类的对象的GetItemAsset()方法，执行了图集的加载方法LoadAtlas()。

```c#
		void LoadAtlas(PackageItem item)
		{
			string ext = Path.GetExtension(item.file);
			string fileName = item.file.Substring(0, item.file.Length - ext.Length);

			Texture tex = null;
			Texture alphaTex = null;
			DestroyMethod dm;

			if (_fromBundle)
			{
				if (_resBundle != null)
				{
#if (UNITY_5 || UNITY_5_3_OR_NEWER)
					tex = _resBundle.LoadAsset<Texture>(fileName);
#else
					tex = (Texture2D)_resBundle.Load(fileName, typeof(Texture2D));
#endif
				}
				else
					Debug.LogWarning("FairyGUI: bundle already unloaded.");

				dm = DestroyMethod.None;
			}
			else
				tex = (Texture)_loadFunc(fileName, ext, typeof(Texture), out dm);

			if (tex == null)
				Debug.LogWarning("FairyGUI: texture '" + item.file + "' not found in " + this.name);
			else if (!(tex is Texture2D))
			{
				Debug.LogWarning("FairyGUI: settings for '" + item.file + "' is wrong! Correct values are: (Texture Type=Default, Texture Shape=2D)");
				tex = null;
			}
			else
			{
				if (((Texture2D)tex).mipmapCount > 1)
					Debug.LogWarning("FairyGUI: settings for '" + item.file + "' is wrong! Correct values are: (Generate Mip Maps=unchecked)");
			}

			if (tex != null)
			{
				fileName = fileName + "!a";
				if (_fromBundle)
				{
					if (_resBundle != null)
					{
#if (UNITY_5 || UNITY_5_3_OR_NEWER)
						alphaTex = _resBundle.LoadAsset<Texture2D>(fileName);
#else
						alphaTex = (Texture2D)_resBundle.Load(fileName, typeof(Texture2D));
#endif
					}
				}
				else
					alphaTex = (Texture2D)_loadFunc(fileName, ext, typeof(Texture2D), out dm);
			}

			if (tex == null)
			{
				tex = NTexture.CreateEmptyTexture();
				dm = DestroyMethod.Destroy;
			}

			if (item.texture == null)
			{
				item.texture = new NTexture(tex, alphaTex, (float)tex.width / item.width, (float)tex.height / item.height);
				item.texture.destroyMethod = dm;
			}
			else
			{
				item.texture.Reload(tex, alphaTex);
				item.texture.destroyMethod = dm;
			}
		}
```

##### 4.获取UnityEngine.Texture数据

使用UnityEngine提供的Resources.Load()方法，或是AssetBundle.LoadAsset()方法，

可以获得这个图集的纹理UnityEngine.Texture。

另外，对于在fairy编辑器中设置了透明通道分离的图集，需多获得一个纹理UnityEngine.Texture类的对象。

如果没有获取到纹理集，则使用NTexture.CreateEmptyTexture()方法创建一个空白的纹理（继承自UnityEngine.Texture的UnityEngine.Texture2D）。

##### 5.创建FairyGUI.NTexture，存储到PackageItem.texture

根据这两个UnityEngine.Texture图集，图片的宽高信息，创建一个FairyGUI.NTexture，存储这些信息。

并将这个FairyGUI.NTexture类的对象，存储到PackageItem.texture字段中。

##### 6.刷新纹理

如果在存储这个FairyGUI.NTexture类的对象时，PackageItem.texture字段已经有值，

则调用NTexture.Reload()方法，来刷新纹理。

（待定，没有被调用过。）

##### 7.将数据传递给Image

在纹理和图片都加载完成之后，回到GImage.ConstructFromResource()方法，继续执行。

将PackageItem.texture的值，这个NTexture数据，传递给，GImage._content这个Image，作为其texture属性存储下来。

##### 8.将数据传递给NGraphics

在设置Image.texture这个属性值时，会调用Image.UpdateTexture()方法，

将这个NTexture值，传递给Image.graphics这个属性（Image.graphics为NGraphics类型），

设置为NGraphics.texture属性值。

### GoWrapper

（待定）




## 坐标系统

### 定位点与锚点

**GObject.pivot**表示此GObject的定位点，这个Vector2的x和y的取值范围为0~1。

**GObject.pivotAsAnchor**可将定位点设置为锚点，而不能脱离定位点去设置锚点。

### 坐标转换

fairy系的坐标系统，原点为左上角，2D坐标系统；

而unity系的坐标系统，为左手3D坐标系统。

#### DisplayObject.LocalToGlobal

将fairy的本地坐标（即相对于FairyGUI.DisplayObject坐标），转换为fairy系的屏幕坐标（如FairyGUI.InputEvent所记录的坐标），可以直接使用DisplayObject.LocalToGlobal方法。

##### 源码

```c#
		public Vector2 LocalToGlobal(Vector2 point)
		{
			Container wsc = this.worldSpaceContainer;

			Vector3 worldPoint = this.cachedTransform.TransformPoint(point.x, -point.y, 0);
			if (wsc != null)
			{
				if (wsc.hitArea is MeshColliderHitTest) //Not supported for UIPainter, use TransfromPoint instead.
					return new Vector2(float.NaN, float.NaN);

				Vector3 screePoint = wsc.GetRenderCamera().WorldToScreenPoint(worldPoint);
				return new Vector2(screePoint.x, Stage.inst.stageHeight - screePoint.y);
			}
			else
			{
				point = Stage.inst.cachedTransform.InverseTransformPoint(worldPoint);
				point.y = -point.y;
				return point;
			}
		}
```

##### 解读

1. 获取到FairyGUI.DisplayObject所记录的坐标(a,b)，它是此DisplayObject相对于其父节点的坐标。

   ![FairyGUI.DisplayObject所记录的坐标](/image-20191027115857206.png)

2. 调整坐标值，得到其unity系本地坐标(a,-b,0)，便于后续利用UnityEngine提供的方法去操纵坐标。

   ![unity系本地坐标](/image-20191027120130070.png)

3. 根据此DisplayObject的cachedTransform属性（UnityEngine.Transform类型）， 使用UnityEngine.Transform.TransformPoint()方法，计算出其unity系世界坐标(d,e,f)。

   ![unity系世界坐标](/image-20191027123807892.png)

4. 此DisplayObject的worldSpaceContainer属性，记录了此DisplayObject的根节点容器Container，使用Container.GetRenderCamera()方法，获取到它的渲染相机，一个UnityEngine.Camera。

5. 根据此UnityEngine.Camera，使用Camera.WorldToScreenPoint()方法，将之前得到的unity系世界坐标(d,e,f)，转化为此相机内的屏幕坐标(g,h,0)。

   ![unity系屏幕坐标](/image-20191027142405611.png)

6. 此屏幕坐标为unity系坐标，若要将其应用于fairy系坐标的计算，还需将其转化为fairy系坐标。[FairyGUI.Stage]Stage.inst这个全局静态变量，记录了屏幕信息。

   ![fairy系屏幕坐标](/image-20191027123716165.png)

7. 最终得到的这个fairy系屏幕坐标，将可以与从FairyGUI.InputEvent中取得的坐标，做计算。

#### 坐标转换方法汇总

**DisplayObject.LocalToGlobal**

**DisplayObject.GlobalToLocal** 

local指局部坐标，fairy的本地坐标，即相对于FairyGUI.DisplayObject坐标。

global指全局坐标，fairy系的屏幕坐标，如FairyGUI.InputEvent所记录的坐标。

**GObject.LocalToRoot**

**GObject.RootToLocal**

如果有UI适配导致的全局缩放，那么逻辑屏幕大小和物理屏幕大小将会不一致。

这里的local还是指局部坐标。

而root将不同于global（物理屏幕坐标），而是指逻辑屏幕坐标。

**DisplayObject.WorldToLocal**

转换世界坐标点到等效的本地xy平面的点。等效的意思是他们在屏幕方向看到的位置一样。

这种需要主要出现在碰撞检测。

**DisplayObject.TransformPoint**

**DisplayObject.TransformRect**

两个DisplayObject之间的坐标转换。




## 事件机制

#### EventDispatcher 事件分发器

从类图可以看出，所有fairy可交互型组件都继承自EventDispatcher。

这样，每种fairy组件，便都能使用事件机制。

#### EventListener 事件接收器

创建事件接收器时，需要一个事件分发器和一个事件名作为构造参数。

![EventListener构造函数](/14.png)

这使得每个事件接收器都对应一个事件分发器，一个事件桥。

![EventListener._bridge](/image-20191025111338305.png)

而一个事件分发器，如GObject，往往，根据需求，会有多个事件接收器作为属性字段，如GObject.onClick，GObject.onRightClick，之类。

#### EventBridge 事件桥

创建事件桥时，需要一个事件分发器作为构造参数。

![EventBridge构造函数](/image-20191024204728335.png)

这使得每个事件桥都对应一个事件分发器。

![EventBridge.owner](/image-20191025111736660.png)

而一个事件分发器，应允许它使用多个事件桥，因此事件分发器中用一个词典记录了事件名-事件桥。

![EventDispatcher._dic](/image-20191024204050292.png)

#### 通过事件接收器注册事件

在业务层，比如给按钮注册点击事件，fairy使用的是**EventListener.Add**之类的方法。

![EventListener.Add](/image-20191025111917222.png)

```c#
		public void Add(EventCallback1 callback)
		{
			_bridge.Add(callback);
		}
```

事件接收器将这个回调函数（代理）作为参数，传递给了自身宿主的事件桥。

![EventBridge.Add](/image-20191025114142835.png)

```c#
		public void Add(EventCallback1 callback)
		{
			_callback1 -= callback;
			_callback1 += callback;
		}
```

事件桥再将这个回调函数存储在自己的字段中，以备使用。

![EventBridge._callback1](/image-20191025114424356.png)

#### 通过事件分发器注册事件

在业务层，有时需要使用事件机制来传递参数，我们一般使用的是**EventDispatcher.AddEventListener**之类的方法。

![EventDispatcher.AddEventListener](/image-20191025130445516.png)

```c#
		public void AddEventListener(string strType, EventCallback1 callback)
		{
			if (strType == null)
				throw new Exception("event type cant be null");

			if (_dic == null)
				_dic = new Dictionary<string, EventBridge>();

			EventBridge bridge = null;
			if (!_dic.TryGetValue(strType, out bridge))
			{
				bridge = new EventBridge(this);
				_dic[strType] = bridge;
			}
			bridge.Add(callback);
		}
```

事件分发器注册事件的逻辑，和事件接收器逻辑基本一致：将回调函数传递给自身记录的事件桥词典，然后由事件桥去存储回调函数。

#### 抛出事件

在业务层，我们抛出自定义事件，一般是使用**EventDispatcher.DispatchEvent**方法。

![EventDispatcher.DispatchEvent](/image-20191025125503784.png)

而事件分发器，会在自身记录的事件桥词典中，索引出这个事件桥，让事件桥去做相关逻辑操作。

![EventBridge.CallInternal](/image-20191025142435303.png)

```c#
		public void CallInternal(EventContext context)
		{
			_dispatching = true;
			context.sender = owner;
			try
			{
				if (_callback1 != null)
					_callback1(context);
				if (_callback0 != null)
					_callback0();
			}
			finally
			{
				_dispatching = false;
			}
		}
```

#### 冒泡机制

##### 源码

而用户的输入操作，fairy使用**EventDispatcher.BubbleEvent**抛出事件。

![EventDispatcher.BubbleEvent](/image-20191025150106569.png)

```c#
		internal bool BubbleEvent(string strType, object data, List<EventBridge> addChain)
		{
			EventContext context = EventContext.Get();
			context.initiator = this;

			context.type = strType;
			context.data = data;
			if (data is InputEvent)
				sCurrentInputEvent = (InputEvent)data;
			context.inputEvent = sCurrentInputEvent;
			List<EventBridge> bubbleChain = context.callChain;
			bubbleChain.Clear();

			GetChainBridges(strType, bubbleChain, true);

			int length = bubbleChain.Count;
			for (int i = length - 1; i >= 0; i--)
			{
				bubbleChain[i].CallCaptureInternal(context);
				if (context._touchCapture)
				{
					context._touchCapture = false;
					if (strType == "onTouchBegin")
						Stage.inst.AddTouchMonitor(context.inputEvent.touchId, bubbleChain[i].owner);
				}
			}

			if (!context._stopsPropagation)
			{
				for (int i = 0; i < length; ++i)
				{
					bubbleChain[i].CallInternal(context);

					if (context._touchCapture)
					{
						context._touchCapture = false;
						if (strType == "onTouchBegin")
							Stage.inst.AddTouchMonitor(context.inputEvent.touchId, bubbleChain[i].owner);
					}

					if (context._stopsPropagation)
						break;
				}

				if (addChain != null)
				{
					length = addChain.Count;
					for (int i = 0; i < length; ++i)
					{
						EventBridge bridge = addChain[i];
						if (bubbleChain.IndexOf(bridge) == -1)
						{
							bridge.CallCaptureInternal(context);
							bridge.CallInternal(context);
						}
					}
				}
			}

			EventContext.Return(context);
			context.initiator = null;
			context.sender = null;
			context.data = null;
			return context._defaultPrevented;
		}
```

其中，调用了EventDispatcher.GetChainBridges这个方法，用来获取这个事件分发器及其所有父节点事件分发器的事件桥。

![EventDispatcher.GetChainBridges](/image-20191025152609736.png)

```c#
		internal void GetChainBridges(string strType, List<EventBridge> chain, bool bubble)
		{
			EventBridge bridge = TryGetEventBridge(strType);
			if (bridge != null && !bridge.isEmpty)
				chain.Add(bridge);

			if ((this is DisplayObject) && ((DisplayObject)this).gOwner != null)
			{
				bridge = ((DisplayObject)this).gOwner.TryGetEventBridge(strType);
				if (bridge != null && !bridge.isEmpty)
					chain.Add(bridge);
			}

			if (!bubble)
				return;

			if (this is DisplayObject)
			{
				DisplayObject element = (DisplayObject)this;
				while ((element = element.parent) != null)
				{
					bridge = element.TryGetEventBridge(strType);
					if (bridge != null && !bridge.isEmpty)
						chain.Add(bridge);

					if (element.gOwner != null)
					{
						bridge = element.gOwner.TryGetEventBridge(strType);
						if (bridge != null && !bridge.isEmpty)
							chain.Add(bridge);
					}
				}
			}
			else if (this is GObject)
			{
				GObject element = (GObject)this;
				while ((element = element.parent) != null)
				{
					bridge = element.TryGetEventBridge(strType);
					if (bridge != null && !bridge.isEmpty)
						chain.Add(bridge);
				}
			}
		}
```

然后去处理这个冒泡链列表内容。

##### 解读规则

1. 从最上层父节点事件分发器开始，处理捕获型事件，依次往下，最后处理这个事件分发器本身所注册的捕获型事件。
2. 最先处理这个事件分发器本身所注册的非捕获型事件，依次往上，处理其父节点事件分发器所注册的非捕获型事件。直到遇到了禁用冒泡的父节点事件分发器，便中断，不再往上冒泡，不再处理上层父节点事件分发器所注册的非捕获型事件。
3. 对于额外加入的冒泡链，只要此事件分发器未禁用冒泡，则依次处理此冒泡链中所有事件分发器的注册事件。

#### EventContext 事件内容

fairy源码提供2种类型的事件回调代理：EventCallback0和EventCallback1。

![EventCallback0](/image-20191025143314318.png)

![EventCallback1](/image-20191025143346163.png)

EventCallback0不带参数，而EventCallback1带EventContext类型参数。

![EventContext](/image-20191025163607801.png)

EventDispatcher EventContext.sender	此事件内容的事件分发器

object EventContext.initiator	此事件内容的创始者（而不可能是父节点事件分发器）

string EventContext.type	事件名

object EventContext.data	自定义数据

InputEvent EventContext.inputEvent	输入信息数据

void EventContext.StopPropagation()	不再往上层冒泡

void EventContext.PreventDefault()	对事件不做响应

void EventContext.CaptureTouch()	触摸事件类型设置为捕获型事件

EventContext EventContext.Get()	取出事件内容池中第一个元素

### 事件流概览

![事件流概览](/image-20191025174106818.png)




## 缓动

### GTween

#### 概览

GTween类是一个工具类，它提供了与缓动相关的一切静态方法、记录了静态字段，供全局调用。

![GTween](/image-20191029114220864.png)

#### 创建缓动的方法

在业务层，创建缓动的方式，是使用GTween.To的多种重载方法和其他方法。

| public class GTween                                          |
| :----------------------------------------------------------- |
| public static GTweener To(float startValue, float endValue, float duration) |
| public static GTweener To(Vector2 startValue, Vector2 endValue, float duration) |
| public static GTweener To(Vector3 startValue, Vector3 endValue, float duration) |
| public static GTweener To(Vector4 startValue, Vector4 endValue, float duration) |
| public static GTweener To(Color startValue, Color endValue, float duration) |
| public static GTweener ToDouble(double startValue, double endValue, float duration) |
| public static GTweener Shake(Vector3 startValue, float amplitude, float duration) |

#### 创建缓动的逻辑

使用GTween.To方法创建缓动时，它调用了TweenManager.CreateTween()方法，并将这个缓动GTweener记录在TweenManager中，便于统一管理。如：

```c#
		public static GTweener To(float startValue, float endValue, float duration)
		{
			return TweenManager.CreateTween()._To(startValue, endValue, duration);
		}
```

### TweenManager

#### 概览

TweenManager用来管理fairy中的所有缓动。

![TweenManager](/image-20191028191338625.png)

#### 主要属性字段

TweenManager._activeTweens 记录了正在活跃的缓动

![TweenManager._activeTweens](/image-20191029093245950.png)

TweenManager._tweenerPool 为缓动的回收池

![TweenManager._tweenerPool](/image-20191029093301743.png)

#### 每帧执行

TweenManager这个静态类内部嵌套一个**TweenEngine**类。

FairyGUI.TweenManager.TweenEngine类继承自UnityEngine.MonoBehaviour，因而包含了unity的Update方法。

```c#
		class TweenEngine : MonoBehaviour
		{
			void Update()
			{
				TweenManager.Update();
			}
		}
```

再由TweenManager在其Init方法中，加载这个TweenEngine这个组件。

```c#
		static void Init()
		{
			_inited = true;
			if (Application.isPlaying)
			{
				GameObject gameObject = new GameObject("[FairyGUI.TweenManager]");
				gameObject.hideFlags = HideFlags.HideInHierarchy;
				gameObject.SetActive(true);
				Object.DontDestroyOnLoad(gameObject);

				gameObject.AddComponent<TweenEngine>();
			}
		}
```

这样，TweenManager.Update方法就会被unity每帧执行。

#### GTweener

当使用TweenManager.CreateTween方法，来创建一个缓动创建了一个GTweener实例。

```c#
		internal static GTweener CreateTween()
		{
			if (!_inited)
				Init();

			GTweener tweener;
			int cnt = _tweenerPool.Count;
			if (cnt > 0)
			{
				tweener = _tweenerPool[cnt - 1];
				_tweenerPool.RemoveAt(cnt - 1);
			}
			else
				tweener = new GTweener();
			tweener._Init();
			_activeTweens[_totalActiveTweens++] = tweener;

			if (_totalActiveTweens == _activeTweens.Length)
			{
				GTweener[] newArray = new GTweener[_activeTweens.Length + Mathf.CeilToInt(_activeTweens.Length * 0.5f)];
				_activeTweens.CopyTo(newArray, 0);
				_activeTweens = newArray;
			}

			return tweener;
		}
```

在Update时，去执行_activeTweens字段中记录的所有GTweener实例的Update方法。

```c#
		internal static void Update()
		{
			int cnt = _totalActiveTweens;
			int freePosStart = -1;
			for (int i = 0; i < cnt; i++)
			{
				GTweener tweener = _activeTweens[i];
				if (tweener == null)
				{
					if (freePosStart == -1)
						freePosStart = i;
				}
				else if (tweener._killed)
				{
					tweener._Reset();
					_tweenerPool.Add(tweener);
					_activeTweens[i] = null;

					if (freePosStart == -1)
						freePosStart = i;
				}
				else
				{
					if ((tweener._target is GObject) && ((GObject)tweener._target)._disposed)
						tweener._killed = true;
					else if (!tweener._paused)
						tweener._Update();

					if (freePosStart != -1)
					{
						_activeTweens[freePosStart] = tweener;
						_activeTweens[i] = null;
						freePosStart++;
					}
				}
			}

			if (freePosStart >= 0)
			{
				if (_totalActiveTweens != cnt) //new tweens added
				{
					int j = cnt;
					cnt = _totalActiveTweens - cnt;
					for (int i = 0; i < cnt; i++)
					{
						_activeTweens[freePosStart++] = _activeTweens[j];
						_activeTweens[j] = null;
						j++;
					}
				}
				_totalActiveTweens = freePosStart;
			}
		}
```

### 其他类与接口

#### GTweener

本文中所说的一个缓动就是一个GTweener类的实例。

[TweenValue] startValue	此缓动的开始帧数据

[TweenValue] endValue	此缓动的结束帧数据

[TweenValue] value	此缓动的当前帧数据

[float] duration	此缓动的过程时长

[object] target	此缓动的作用目标

[TweenPropType] _propType	此缓动的属性类型

[EaseType] _easeType	此缓动的类型

[GTweenCallback] _onUpdate	此缓动的回调委托

[bool] _paused	当前暂停状态

[GPath] _path	目前没有使用

![GTweener](/image-20191028194819824.png)

#### TweenValue

TweenValue用于缓动的帧的数据。

![TweenValue](/image-20191028195032375.png)

#### ITweenListener

ITweenListener是缓动侦听接口。

![ITweenListener](/image-20191028183227430.png)

一些有缓动需求的类实现了此接口。

![实现ITweenListener接口的类](/image-20191029172135379.png)

在GTweener中记录了一个ITweenListener类型的_listener字段。

![GTweener._listener](/image-20191029180738619.png)

在GTweener中合适的时机去调用执行它的各种方法。

### 缓动的逻辑算法

##### 算法出处

在GTweener.Update()方法中，调用了EaseManager.Evaluate()方法，用数学计算的方式，来获取缓动的当前数值。

EaseManager提供了多种缓动类型的计算。

> EaseManager为引进的代码，此C#代码的主要作者为[Daniele Giardini](http://dotween.demigiant.com/license.php)，少部分缓动方程来自[Robert Penner](http://robertpenner.com/easing)。

打开Daniele Giardini的个人网站会发现，fairy的缓动计算公式，即**DOTween**。

##### 缓动类型

缓动类型记录在**EaseType**这个枚举中。

缓动类型效果示例：[ Ease Visualizer ](https://greensock.com/ease-visualizer)

缓动类型图解：![缓动类型图解](/image-20191029163457501.png)

### fairy自带的缓动功能汇总

逻辑程序员编写代码调用GTween.To等方法，可以创建一个缓动；

fairy在编辑器中提供了一些便捷操作，让UE可以直接控制缓动，之后再动态创建出来。

在编辑器中有3种创建缓动的方式：

#### 给组件创建动效

给组件创建动效Transition，能创建多个缓动，并灵活地控制它们。

![给组件创建动效](/image-20191029145743318.png)

#### 对元件的属性控制启用缓动

给一个组件创建了控制器之后，可以对其元件设置属性控制。

![元件的属性控制](/image-20191029150023870.png)

勾选缓动之后，在创建此GearBase时，创建了一个GearTweenConfig对象，赋值给了此GearBase的_tweenConfig属性。

在GearBase这个抽象类中，有个Apply抽象方法。当控制器跳转页签时，会执行此Apply方法。

GearBase的各个子类复写了这个方法。

以GearXY.Apply()方法为例：

```c#
		override public void Apply()
		{
			GearXYValue gv;
			if (!_storage.TryGetValue(_controller.selectedPageId, out gv))
				gv = _default;

			if (_tweenConfig != null && _tweenConfig.tween && UIPackage._constructing == 0 && !disableAllTweenEffect)
			{
				if (_tweenConfig._tweener != null)
				{
					if (_tweenConfig._tweener.endValue.x != gv.x || _tweenConfig._tweener.endValue.y != gv.y)
					{
						_tweenConfig._tweener.Kill(true);
						_tweenConfig._tweener = null;
					}
					else
						return;
				}

				if (_owner.x != gv.x || _owner.y != gv.y)
				{
					if (_owner.CheckGearController(0, _controller))
						_tweenConfig._displayLockToken = _owner.AddDisplayLock();

					_tweenConfig._tweener = GTween.To(_owner.xy, new Vector2(gv.x, gv.y), _tweenConfig.duration)
						.SetDelay(_tweenConfig.delay)
						.SetEase(_tweenConfig.easeType)
						.SetTarget(this)
						.SetListener(this);
				}
			}
			else
			{
				_owner._gearLocked = true;
				_owner.SetXY(gv.x, gv.y);
				_owner._gearLocked = false;
			}
		}
```

#### 代码调用进度条的动态变化

调用GProgressBar.TweenValue方法，在进度条的进度变化时播放一个缓动。

```c#
		public GTweener TweenValue(double value, float duration)
		{
			double oldValule;

			GTweener twener = GTween.GetTween(this, TweenPropType.Progress);
			if (twener != null)
			{
				oldValule = twener.value.d;
				twener.Kill(false);
			}
			else
				oldValule = _value;

			_value = value;
			return GTween.ToDouble(oldValule, _value, duration)
				.SetEase(EaseType.Linear)
				.SetTarget(this, TweenPropType.Progress);
		}
```





# UE相关



## 组件

UE所使用的组件，可交互型组件，一般都继承自GObject。

可以顾名思义，在上文可交互类型组件的类图中，找到它所对应的类。



## 控制器

### Controller

一个控制器即为一个Controller类的实例。

![Controller](/image-20191028180324311.png)

### 属性控制

在fairy元件的属性控制栏，可以设置其在此控制器下的显示控制。

![控制器的显示控制](/image-20191028155801183.png)

除此之外，fairy还提供了多种属性控制类型。

![控制器的属性控制](/image-20191028155921772.png)

每种属性控制，都是一种GearBase类型的子类。

![GearBase](/image-20191029211054678.png)

在上文控制器的缓动类图中，能找到其对应的类。

### 控制器的动作

在修改控制器面板中，可添加的动作**ControllerAction**，动作类型均来自其子类。

![修改控制器](/image-20191029210754358.png)

播放动效，相关代码在**PlayTransitionAction**。

改变其他控制器页面，相关代码在**ChangePageAction**。



## 动效

### Transition

一个动效，就是一个Transition类的实例。

![给组件创建动效](/image-20191029145743318.png)

Transition类如下：

![Transition](/image-20191028180527450.png)

### TransitionItem

在fairy编辑器的动效编辑窗口中，每个图层都对应一个TransitionItem类的实例，记录在Transition._items字段中。

![TransitionItem](/image-20191029203750733.png)

TransitionItem的tweenConfig字段为TweenConfig类型，记录了其缓动数据。

![TweenConfig](/image-20191029204017263.png)

TransitionItem的value字段为object类型，在构造时，会根据其[TransitionActionType]type字段，为其创建不同类型的数据。

![TValue](/image-20191029204605102.png)



## 关联















