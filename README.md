One����ܰ�������ʲô��
 
One��ܷ�Ϊ������Ŀ��OneCoreΪ���Ĺ��̣���Ϊlib�⵼�룻androidOneΪ��ʾ��Ŀ��

One�������ΪMVCģʽ�������android frameworkΪ���ģ�����Android�����е���������ѡ�ͣ�
��Pragmatic����AndroidӦ�òο�ʾ������android��Ŀ���ʵ�����ܽ�����ʾ��
�ԡ����ӵ������һ���͹��ˡ�Ϊ�����־����Android������Ա���ٴһ���򵥸�Ч��android������ܣ�


�첽ģ�飺
��װAsyncTask�࣬���첽��ܵ����������ҳ��ͨ��ʵ�ֻص�������ȡ���ݲ�ֱ�Ӹ���UI������ʵ�ֶ��̻߳��ƣ�֧�ֲ�����������������ȴ���
����һ����BaseActivity��BaseFragment��ʵ�֡�
 
 
ʹ�����£�
��BaseActivity��onCreate������ʼ����
mAsyncTaskManager = AsyncTaskManager.getInstance(mContext);
 
ʵ�����·�����
/**
 * ����������Ҫ������磩
 * @param requsetCode ������
 */
public void request(int requsetCode){
    mAsyncTaskManager.request(requsetCode, this);
}
 
/**
 * ��������
 * @param requsetCode ������
 * @param isCheckNetwork �Ƿ��������磬true��飬false�����
 */
public void request(int requsetCode, boolean isCheckNetwork){
    mAsyncTaskManager.request(requsetCode, isCheckNetwork, this);
}
 
/**
 * ȡ������
 * @param requsetCode
 */
public void cancelRequest(int requsetCode){
    mAsyncTaskManager.cancelRequest(requsetCode);
}
 
/**
 * ȡ����������
 */
public void cancelRequest(){
    mAsyncTaskManager.cancelRequest();
}
 
@Override
public Object doInBackground(int requestCode) throws HttpException{
    return null;
}
 
@Override
public void onSuccess(int requestCode, Object result) {
 
}
 
@Override
public void onFailure(int requestCode, int state, Object result) {
    switch(state){
        //���粻���ø�����ʾ
        case AsyncTaskManager.HTTP_NULL_CODE:
            break;
 
        //���������������ʾ
         case AsyncTaskManager.HTTP_ERROR_CODE:
            break;
 
        //���������������ʾ
        case AsyncTaskManager.REQUEST_ERROR_CODE:
            break;
    }    
}


HTTP����ģ�飺
���õ�����AsyncHttpClient�������ڴ˻���������ͬ��������������ࣨ����첽���ʹ�ã���֧��http��https��ʽ��֧��get��post��put��delete������֧��GZIP��File��ʽ��֧��Retry��Cacel���ԣ�����������
 
Commonģ�飺
ҳ���ջ�����������ϵͳ�쳣����SharedPreferences����LruCache��������ҳ�洫�������Ҳ��õ����ͷ����⣩��Json�����������xml�����������SoapObject�����������
 
DBģ�飺
����GreenDao������ֱ��ʵ��Java Object��CURD�����Ϳ��Բ������ݿ⡣ 
����java�����Զ�����model��dao��session����ȴ��룬������ֱ��ʹ�ü��ɡ�
����DBManager�࣬�������ݲ���ֻ��Ҫ��ȡDBManagerʵ������ȡDaoSession��Ȼ��ͨ��DaoSession����ȡ����Ҫ������dao���ɡ�

ʹ�����£�
dao = DBManager.getInstance(mContext).getDaoSession().getNoteDao();
 
��Դ����ģ�飺
�ڵ�����AsyncHttpClient��������BreakpointHttpResponseHandler�֧࣬�ֶಢ�������ļ��ϴ����ϵ���������ͣ��������ɾ����������
 
ʹ�����£�
 downloadMgr = DownloadManager.getInstance();
     downloadMgr.setDownLoadCallback(new DownLoadCallback() {
 
        @Override
        public void onLoading(String url, int bytesWritten, int totalSize) {
            super.onLoading(url, bytesWritten, totalSize);
        }
 
        @Override
        public void onSuccess(String url, String filePath) {
            super.onSuccess(url, filePath);
        }
 
        @Override
        public void onFailure(String url, String strMsg) {
            super.onFailure(url, strMsg);
        }
    });
 
    //�����������
    for (DownloadInfo bean1 : list) {
        downloadMgr.addHandler(bean1.getUrl());
    }
 
ͼƬ����ģ�飺
����universal-image-loader����������й�ʹ�������μ�universal-image-loader������Ϣ����������github��ַ��https://github.com/nostra13/Android-Universal-Image-Loader
 
�������������������С����Ƕ������˰ɣ��Ͽ춯�����԰ɣ�
����ʹ����ο�androidOne��ʾ���̡�
 
�Ҹı䲻��������磡�������Ҳ��Ϣ���Ҹı䣡
 
����κ�������߽��飬��ӭ��ͨ��
2891429357@qq.com