# ��Դ������

## �༭����

> ����Դ���б��飬������Դ���԰�����м��أ����ò�����Դ��Դ����Щassetbundle��ͨ����Դ������������ÿ����Դ����Ψһ��ַ������Դ�ƶ�ɾ���Ȳ�����ʱ����Զ�����Դ�������ӵ��µ���Դ��ͬʱ֧�ֱ༭����ʹ�ô���Ͳ����assetbundle�ķ�ʽ���У�������ʱ�л���

��Դ���ط�ʽ���������Լ��Զ���

## �༭��ʹ��

��window/ResMgr �˵�����������
> ![Alt text](./1571800905844.png)
> ��Դ����������


### ��Դ����������

**��Դ��**: 
����Դ���������������Դ�����
�Ҽ�������Ŀհ�λ�ÿ������һ���µ���Դ�飬��Դ�����ֶ���Ψһ�ģ���������ѡ����Դ��ѡ�к��Ҽ����Ը�������ɾ��

**��Դ��Ϣ**: 
�Ҳ��ϰ벿�����㵱ǰѡ�е���Դ������ѡ�е���Դ��ϢĿǰֻ�� ����`��Դ�Ƿ�פ�ڴ�`
>`�ر�˵��:` ��Դ��url���ɹ���Ϊ resource�µ�urlΪr://folderName/1.prefab �����ĸ�ʽ   abĿ¼�µ����ⲿ�ļ���·��Ϊ��·��
>���磺![Alt text](./1571801116798.png)
>Cube_b.prefab��urlΪ e://New Folder/Cube_b.prefab

**��Դ�б�**��
�Ҳ��°벿������ѡ�е���Դ�������������Դ�б�
˫����Դ�б��������Դ����ѡ�й���������ļ�
���ε��������޸���Դ��Ψһ��ַ�����ʱĬ�ϵ���Դ��ַΪ ��Դ��_��Դ����׺

> ` ע��:`
> ��Դ��ַ��ȫ��Ψһ��
> ����ѡ��פ�ڴ����Դ����Զ�����ͷ�


**�����Դ **�� ����ѡ����Դ������Դ����Դ�б�Ŀհ״��Ͽ��԰����Ͻ�������Դ��ӵ���Դ�飬Ҳ֧�������ļ���

> `ע�⣺` �����ļ��е�ʱ��ֻ��ѵ�ǰ�ļ����µ���Դ��ӵ���Դ�飬����������ļ���Դ

### �༭���Զ���ӿ� 
YKFramwork.ResMgr.Editor.IResConfig 
``` cs
string JsonFilePath { get; } //��Դjson�ļ�����·��
string ExternalResDir { get; } //Ҫ�����assetbundle���ⲿ�ļ���
List<Type> CanDropType { get; } //������Դ���������ϵ��ļ�����
```

���������ʵ�ֽӿ�Ȼ���޸�resconfig����������������Ĭ�ϵ�
![Alt text](./1571799514142.png)

Ĭ����һ��Ĭ��ʵ��

### ������Դ����
> ![Alt text](./1571799654136.png)


���Ϊ�༭�������õ�����Դ��ab

�Ҳ�Ϊѡ�е�ab�����������Դ��Ϣ

> AB Ϊÿ��Ŀ¼������һ��ab
> ������ͼ��Դ�ṹ:
> ![Alt text](./1571799825969.png)
>> �ͻ����ɣ� 
> new folder.bytes ->����  cube_b mainCame... �ȵ� (ǰ������Դ����������������Դ��Ȼ���ᱻ�����ab)
> new folder_new folder.bytes
> new folder 1.bytes
>new folder 2.bytes

>` ע�⣺` ab���ֻ���ExternalResDir Ϊ��Ŀ¼  Ȼ������е�/����_Ϊ����

## ��Դ����
���ResMgr�ű�����ĳ�����Ϸ������ע���л���������ɾ��

ʵ��YKFramwork.ResMgr.IResLoadCfg ���Զ�����ļ�������

```
  bool SimulateAssetBundle { get; } //�Ƿ�򿪱༭����ab���ط�ʽ
  ResJsonData ResData { get; }//��Դ���ñ����� //�����Ҫ�Լ��ȼ��غ�
  string RootABPath { get; } //ab��ŵĸ�Ŀ¼
  string RootABUrl { get; } //ab��ŵ�Ŀ¼��url
  string AssetBundleVariant { get; }//ab�ĺ�׺����
```
ͬ�����Ҳ��һ��Ĭ��ʵ�� YKFramwork.ResMgr.DefResLoadCfg����Ա�д�Լ���config

��ôʹ�� 

�Ƚ������ñ��ʼ��
![Alt text](./1571801907706.png)
��ʼ����Ϳ���ʹ��  resmgr ��Api��


### ��Ҫ API ˵��

YKFramwork.ResMgr.ResMgr��
```
HasAsset(string address) //�ж���Դ�Ƿ����ڴ���

GetRes(string address) //ͬ����ȡһ����Դ�������Դ�����Ǽ��ع��ķ��򱨴�
GetResByUrl(string url)//����һ��һ��ֻ��ʹ��url���л�ȡ

GetResAsync(string address, Action<UnityEngine.Object> callback) //�첽��ȡһ����Դ�������Դ������û�м��ع���

GetResAsyncByUrl (string url, Action<UnityEngine.Object> callback) //����һ����ֻͬ��ʹ��url

LoadGroup(string groupName, Action<string> completed, Action<float, string> itemCompleted)//����һ����Դ �����ֱ�Ϊ ��Դ�����ƣ�������ɣ������굥����Դ�Ļص��������Ⱥ͵�ǰ���س�������Դ��


LoadForResource(string addr, Action<UnityEngine.Object> callback)//����һ��resource�µ���Դ
LoadForResourceByUrl(string url, Action<UnityEngine.Object> callback)//ͬ��


LoadForAB(string addr, Action<UnityEngine.Object> callback,bool releaseAB = false)//��ab�������һ����Դ  releaseAB��־Ϊ���غ��Ƿ��ͷŵ�ab

Release(string addr, bool force = false)//�ͷ�һ����Դ force ǿ���ͷţ�������û�������ط�����ǿ��ж��

UnloadUnused() //��������������ͷ����в��ǳ�פ�ڴ����Դ
```

**�ӿڣ�**

```
YKFramwork.ResMgr.IAssetBundleLoad ����ab��ʵ��

����YKFramwork.ResMgr.ResMgr.Instace.ABMgr =  new DefAssetBundleLoad(); ������
Ĭ��ʵ��Ϊ YKFramwork.ResMgr.DefAssetBundleLoad


YKFramwork.ResMgr.IResourceLoad ����resource��ʵ��
����YKFramwork.ResMgr.ResMgr.Instace.ResourceLoad =  new DefResourceLoad(); ������
Ĭ��ʵ��Ϊ YKFramwork.ResMgr.DefResourceLoad



YKFramwork.ResMgr.IResLoadCfg ���ص�������Ϣ
����  cfg = new DefResLoadCfg();
        ResMgr.Instance.cfg = cfg;
Ĭ��ʵ�� YKFramwork.ResMgr.DefResLoadCfg
```
## ����
��Example�ļ������а��������ͽű�




