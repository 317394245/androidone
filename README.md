One����ܰ�������ʲô��
 
One��ܷ�Ϊ������Ŀ��OneCoreΪ���Ĺ��̣���Ϊlib�⵼�룻androidOneΪ��ʾ��Ŀ��

One�������ΪMVCģʽ�������android frameworkΪ���ģ�����Android�����е���������ѡ�ͣ�
��Pragmatic����AndroidӦ�òο�ʾ������android��Ŀ���ʵ�����ܽ�����ʾ��
�ԡ����ӵ������һ���͹��ˡ�Ϊ�����־����Android������Ա���ٴһ���򵥸�Ч��android������ܣ�


�첽ģ�飺<br/>
��װAsyncTask�࣬���첽��ܵ����������ҳ��ͨ��ʵ�ֻص�������ȡ���ݲ�ֱ�Ӹ���UI������ʵ�ֶ��̻߳��ƣ�֧�ֲ�����������������ȴ���
����һ����BaseActivity��BaseFragment��ʵ�֡�
 
 
ʹ�����£�<br/>
��BaseActivity��onCreate������ʼ����
mAsyncTaskManager = AsyncTaskManager.getInstance(mContext);
 
 
ʵ�����·�����<br/>
public void request(int requsetCode){<br/>
    mAsyncTaskManager.request(requsetCode, this);<br/>
}
 
public void request(int requsetCode, boolean isCheckNetwork){<br/>
    mAsyncTaskManager.request(requsetCode, isCheckNetwork, this);<br/>
}
 
public void cancelRequest(int requsetCode){<br/>
    mAsyncTaskManager.cancelRequest(requsetCode);<br/>
}
 
public void cancelRequest(){<br/>
    mAsyncTaskManager.cancelRequest();<br/>
}
 
@Override
public Object doInBackground(int requestCode) throws HttpException{<br/>
    return null;<br/>
}
 
@Override
public void onSuccess(int requestCode, Object result) {<br/>
 <br/>
}
 
@Override
public void onFailure(int requestCode, int state, Object result) {<br/>
<br/>
}


HTTP����ģ�飺<br/>
���õ�����AsyncHttpClient�������ڴ˻���������ͬ��������������ࣨ����첽���ʹ�ã���֧��http��https��ʽ��֧��get��post��put��delete������֧��GZIP��File��ʽ��֧��Retry��Cacel���ԣ�����������
 
 
Commonģ�飺<br/>
ҳ���ջ�����������ϵͳ�쳣����SharedPreferences����LruCache��������ҳ�洫�������Ҳ��õ����ͷ����⣩��Json�����������xml�����������SoapObject�����������
 
 
DBģ�飺<br/>
����GreenDao������ֱ��ʵ��Java Object��CURD�����Ϳ��Բ������ݿ⡣ 
����java�����Զ�����model��dao��session����ȴ��룬������ֱ��ʹ�ü��ɡ�
����DBManager�࣬�������ݲ���ֻ��Ҫ��ȡDBManagerʵ������ȡDaoSession��Ȼ��ͨ��DaoSession����ȡ����Ҫ������dao���ɡ�


ʹ�����£�<br/>
dao = DBManager.getInstance(mContext).getDaoSession().getNoteDao();
 
 
��Դ����ģ�飺<br/>
�ڵ�����AsyncHttpClient��������BreakpointHttpResponseHandler�֧࣬�ֶಢ�������ļ��ϴ����ϵ���������ͣ��������ɾ����������
 
 
ʹ�����£�<br/>
 downloadMgr = DownloadManager.getInstance();<br/>
     downloadMgr.setDownLoadCallback(new DownLoadCallback() {<br/>
 	 <br/>
        @Override<br/>
        public void onLoading(String url, int bytesWritten, int totalSize) {<br/>
            super.onLoading(url, bytesWritten, totalSize);<br/>
        }<br/>
 
        @Override<br/>
        public void onSuccess(String url, String filePath) {<br/>
            super.onSuccess(url, filePath);<br/>
        }<br/>
 
        @Override<br/>
        public void onFailure(String url, String strMsg) {<br/>
            super.onFailure(url, strMsg);<br/>
        }<br/>
    });
 
    //�����������<br/>
    for (DownloadInfo bean1 : list) {<br/>
        downloadMgr.addHandler(bean1.getUrl());<br/>
    }
 
 
ͼƬ����ģ�飺<br/>
����universal-image-loader����������й�ʹ�������μ�universal-image-loader������Ϣ��
github��ַ��https://github.com/nostra13/Android-Universal-Image-Loader
 
�������������������С����Ƕ������˰ɣ��Ͽ춯�����԰ɣ�
����ʹ����ο�androidOne��ʾ���̡�
 
�Ҹı䲻��������磡�������Ҳ���뽫�Ҹı䣡
 
����κ�������߽��飬��ӭ��ͨ��<br/>
2891429357@qq.com