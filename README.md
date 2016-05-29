# Android-Net-status
获取网络情况

 /**
     * 当前网络
     *
     * @param context
     * @return
     */
    public static int getAPNType(Context context) {

        int netType = -1;

        ConnectivityManager connMgr = (ConnectivityManager) context
                .getSystemService(Context.CONNECTIVITY_SERVICE);

        NetworkInfo networkInfo = connMgr.getActiveNetworkInfo();
        if (networkInfo == null) {

            netType = Constant.NETWORKTYPE_INVALID;
            return netType;
        }
        int nType = networkInfo.getType();
        if (nType == ConnectivityManager.TYPE_MOBILE) {
            return netType = Constant.NETWORKTYPE_2G_3G;
        } else if (nType == ConnectivityManager.TYPE_WIFI) {
            return netType = Constant.NETWORKTYPE_WIFI;
        } else {
            return netType = Constant.NETWORKTYPE_INVALID;
        }

    }



    
    /**
     * 检查网络状态
     *
     * @param cx
     * @return 0：没联网；1：wifi；2：运营商网络
     */
    public static int checkNetworkStatus(Context cx) {
        int status = 0;
        ConnectivityManager cm = (ConnectivityManager) cx
                .getSystemService(Context.CONNECTIVITY_SERVICE);
        NetworkInfo info = cm.getActiveNetworkInfo();

        if (info == null || info.getTypeName() == null || !info.isConnected()) {
            status = 0;
        } else if (info.getTypeName().equalsIgnoreCase("WIFI")) {
            status = 1;
        } else {
            status = 2;
        }

        return status;
    }
