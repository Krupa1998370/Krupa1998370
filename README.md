- 👋 Hi, I’m @Krupa1998370
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
1	package org.cocos2dx.lua; 
2	 
3	import android.annotation.SuppressLint; 
4	import android.content.BroadcastReceiver; 
5	import android.content.ClipData; 
6	import android.content.ClipboardManager; 
7	import android.content.ComponentName; 
8	import android.content.ContentResolver; 
9	import android.content.Context; 
10	import android.content.DialogInterface; 
11	import android.content.Intent; 
12	import android.content.IntentFilter; 
13	import android.content.pm.PackageInfo; 
14	import android.content.pm.PackageManager; 
15	import android.database.Cursor; 
16	import android.graphics.Bitmap; 
17	import android.graphics.BitmapFactory; 
18	import android.media.AudioRecord; 
19	import android.net.ConnectivityManager; 
20	import android.net.NetworkInfo; 
21	import android.net.Uri; 
22	import android.net.wifi.WifiInfo; 
23	import android.net.wifi.WifiManager; 
24	import android.os.Build; 
25	import android.os.Bundle; 
26	import android.os.Handler; 
27	import android.os.Looper; 
28	import android.os.Message; 
29	import android.os.PowerManager; 
30	import android.os.RemoteException; 
31	import android.provider.ContactsContract; 
32	import android.provider.MediaStore; 
33	import android.telephony.PhoneStateListener; 
34	import android.telephony.SignalStrength; 
35	import android.telephony.TelephonyManager; 
36	import android.util.Log; 
37	import android.view.View; 
38	import com.adjust.sdk.Adjust; 
39	import com.adjust.sdk.AdjustConfig; 
40	import com.adjust.sdk.AdjustEvent; 
41	import com.adjust.sdk.LogLevel; 
42	import com.adjust.sdk.OnDeviceIdsRead; 
43	import com.android.installreferrer.api.InstallReferrerClient; 
44	import com.android.installreferrer.api.InstallReferrerStateListener; 
45	import com.android.installreferrer.api.ReferrerDetails; 
46	import com.facebook.e; 
47	import com.google.firebase.analytics.FirebaseAnalytics; 
48	import java.io.BufferedOutputStream; 
49	import java.io.File; 
50	import java.io.FileNotFoundException; 
51	import java.io.FileOutputStream; 
52	import java.math.BigDecimal; 
53	import java.util.ArrayList; 
54	import java.util.Currency; 
55	import java.util.HashMap; 
56	import java.util.Timer; 
57	import java.util.TimerTask; 
58	import org.cocos2dx.lib.Cocos2dxActivity; 
59	import org.cocos2dx.lib.Cocos2dxLuaJavaBridge; 
60	import org.cocos2dx.thirdparty.ThirdDefine; 
61	import org.cocos2dx.thirdparty.ThirdParty; 
62	import org.cocos2dx.utils.ConstDefine; 
63	import org.cocos2dx.utils.MP3Recorder; 
64	import org.cocos2dx.utils.PermissionsUtils; 
65	import org.cocos2dx.utils.ScreenShotListenManager; 
66	import org.cocos2dx.utils.Utils; 
67	import org.json.JSONArray; 
68	import org.json.JSONException; 
69	import org.json.JSONObject; 
70	 
71	/* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/4.dex */ 
72	public class AppActivity extends Cocos2dxActivity { 
73	    private static final String AF_DEV_KEY = "YQRbmP4fZt5LeYmwggJcSV"; 
74	    public static final int PERMISSIONS_DENIED = 1; 
75	    public static final int PERMISSIONS_GRANTED = 0; 
76	    private static final int PICK_PERMS_REQUEST = 0; 
77	    public static Context STATIC_REF = null; 
78	    private static String UserNation = ""; 
79	    public static final String g_LuaTakeScreenShot = "g_takeScreenShot"; 
80	    public static final String g_LuaToastFun = "g_NativeToast"; 
81	    public static String hostIPAdress = "0.0.0.0"; 
82	    public static AppActivity instance = null; 
83	    public static FirebaseAnalytics mFirebaseAnalytics = null; 
84	    private static int m_nBatteryLevel = 100; 
85	    private static int m_nNetStatus = 3; 
86	    private static MP3Recorder recorder = null; 
87	    private static String referrerUrl = null; 
88	    public static String sdfsdg = ""; 
89	    private static String stringStatus; 
90	    private static String stringType; 
91	    public com.facebook.e callbackManager; 
92	    private com.facebook.f0.g logger; 
93	    private InstallReferrerClient referrerClient; 
94	    private Handler m_hHandler = null; 
95	    private PowerManager.WakeLock mWakeLock = null; 
96	    private ThirdParty.OnLoginListener m_LoginListener = null; 
97	    private ThirdParty.OnShareListener m_ShareListener = null; 
98	    private BatteryChangedReceiver batteryChangedReceiver = null; 
99	    public n __CellularListener = null; 
100	    private int m_nPickImgCallFunC = -1; 
101	    private int m_nThirdPayCallFunC = -1; 
102	    private int m_nThirdLoginFunC = -1; 
103	    private int m_nShareFunC = -1; 
104	    private int m_nPayListFunC = -1; 
105	    private int m_nLocationFunC = -1; 
106	    private int m_nContactFunC = -1; 
107	    private int m_nDelAuthorizationFunC = -1; 
108	    private int m_nGetCopyDataFunC = -1; 
109	    private WifiInfo wifiInfo = null; 
110	    private WifiManager wifiManager = null; 
111	    private ScreenShotListenManager mScreenListenManager = null; 
112	    private String m_szLaunchData = ""; 
113	    private String m_szDeviceToken = ""; 
114	    private int m_nsetDragButton = -1; 
115	    private JSONObject m_alertJson = null; 
116	    private String[] permissions = {"android.permission.WRITE_EXTERNAL_STORAGE", "android.permission.READ_EXTERNAL_STORAGE"}; 
117	    PermissionsUtils.IPermissionsResult permissionsResult = new i(); 
118	 
119	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
120	    public class BatteryChangedReceiver extends BroadcastReceiver { 
121	        public BatteryChangedReceiver() { 
122	        } 
123	 
124	        @Override // android.content.BroadcastReceiver 
125	        public void onReceive(Context context, Intent intent) { 
126	            if (intent.getAction().equalsIgnoreCase("android.intent.action.BATTERY_CHANGED")) { 
127	                int unused = AppActivity.m_nBatteryLevel = intent.getIntExtra("level", -1); 
128	            } 
129	        } 
130	    } 
131	 
132	    /* JADX INFO: Access modifiers changed from: package-private */ 
133	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
134	    public class a implements Runnable { 
135	        final /* synthetic */ String j; 
136	        final /* synthetic */ String k; 
137	 
138	        a(String str, String str2) { 
139	            this.j = str; 
140	            this.k = str2; 
141	        } 
142	 
143	        @Override // java.lang.Runnable 
144	        public void run() { 
145	            Cocos2dxLuaJavaBridge.callLuaGlobalFunctionWithString(this.j, this.k); 
146	        } 
147	    } 
148	 
149	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
150	    class b implements DialogInterface.OnClickListener { 
151	        b() { 
152	        } 
153	 
154	        @Override // android.content.DialogInterface.OnClickListener 
155	        public void onClick(DialogInterface dialogInterface, int i) { 
156	            Log.i(ConstDefine.TAG, "DragButton 按钮点击方法的重写"); 
157	            Message obtain = Message.obtain(); 
158	            obtain.what = ConstDefine.DragFloatAction_Back; 
159	            obtain.obj = "back"; 
160	            AppActivity.instance.sendMessageWith(obtain); 
161	            AppActivity.instance.disShowDragbutton(); 
162	        } 
163	    } 
164	 
165	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
166	    class c implements DialogInterface.OnClickListener { 
167	        c() { 
168	        } 
169	 
170	        @Override // android.content.DialogInterface.OnClickListener 
171	        public void onClick(DialogInterface dialogInterface, int i) { 
172	            Log.i(ConstDefine.TAG, "DragButton 取消了AlertDialog"); 
173	        } 
174	    } 
175	 
176	    /* JADX INFO: Access modifiers changed from: package-private */ 
177	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
178	    public class d implements OnDeviceIdsRead { 
179	        d() { 
180	        } 
181	 
182	        @Override // com.adjust.sdk.OnDeviceIdsRead 
183	        public void onGoogleAdIdRead(String str) { 
184	            AppActivity.sdfsdg = str; 
185	        } 
186	    } 
187	 
188	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
189	    class e implements View.OnSystemUiVisibilityChangeListener { 
190	        e() { 
191	        } 
192	 
193	        @Override // android.view.View.OnSystemUiVisibilityChangeListener 
194	        public void onSystemUiVisibilityChange(int i) { 
195	            AppActivity.this.hideNavigationBarDDD(); 
196	        } 
197	    } 
198	 
199	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
200	    class f implements ScreenShotListenManager.OnScreenShotListener { 
201	        f() { 
202	        } 
203	 
204	        @Override // org.cocos2dx.utils.ScreenShotListenManager.OnScreenShotListener 
205	        public void onShot(String str) { 
206	            AppActivity.this.toLuaGlobalFunC(AppActivity.g_LuaTakeScreenShot, str); 
207	        } 
208	    } 
209	 
210	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
211	    class g extends TimerTask { 
212	        g() { 
213	        } 
214	 
215	        @Override // java.util.TimerTask, java.lang.Runnable 
216	        public void run() { 
217	            Message message; 
218	            if (AppActivity.getNetWorkType(AppActivity.instance) == 1) { 
219	                AppActivity appActivity = AppActivity.this; 
220	                appActivity.wifiInfo = appActivity.wifiManager.getConnectionInfo(); 
221	                int rssi = AppActivity.this.wifiInfo.getRssi(); 
222	                if (rssi > 0 || rssi < -50) { 
223	                    int i = 23; 
224	                    if (rssi < -50 && rssi >= -70) { 
225	                        message = new Message(); 
226	                    } else if (rssi >= -70 || rssi < -80) { 
227	                        i = 24; 
228	                        message = (rssi >= -80 || rssi < -100) ? new Message() : new Message(); 
229	                    } else { 
230	                        message = new Message(); 
231	                    } 
232	                    message.what = i; 
233	                } else { 
234	                    message = new Message(); 
235	                    message.what = 22; 
236	                } 
237	                AppActivity.this.m_hHandler.sendMessage(message); 
238	            } 
239	        } 
240	    } 
241	 
242	    /* JADX INFO: Access modifiers changed from: package-private */ 
243	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
244	    public class h implements InstallReferrerStateListener { 
245	        h() { 
246	        } 
247	 
248	        public void onInstallReferrerServiceDisconnected() { 
249	        } 
250	 
251	        public void onInstallReferrerSetupFinished(int i) { 
252	            if (i != 0) { 
253	                return; 
254	            } 
255	            try { 
256	                ReferrerDetails installReferrer = AppActivity.this.referrerClient.getInstallReferrer(); 
257	                String unused = AppActivity.referrerUrl = installReferrer.getInstallReferrer(); 
258	                Log.v(ConstDefine.TAG, "referrerUrl:" + AppActivity.referrerUrl); 
259	                long referrerClickTimestampSeconds = installReferrer.getReferrerClickTimestampSeconds(); 
260	                Log.v(ConstDefine.TAG, "referrerClickTime:" + referrerClickTimestampSeconds); 
261	                long installBeginTimestampSeconds = installReferrer.getInstallBeginTimestampSeconds(); 
262	                Log.v(ConstDefine.TAG, "appInstallTime:" + installBeginTimestampSeconds); 
263	                long referrerClickTimestampServerSeconds = installReferrer.getReferrerClickTimestampServerSeconds(); 
264	                Log.v(ConstDefine.TAG, "referrerClickServerTime:" + referrerClickTimestampServerSeconds); 
265	                long installBeginTimestampServerSeconds = installReferrer.getInstallBeginTimestampServerSeconds(); 
266	                Log.v(ConstDefine.TAG, "appInstallServerTime:" + installBeginTimestampServerSeconds); 
267	                String installVersion = installReferrer.getInstallVersion(); 
268	                Log.v(ConstDefine.TAG, "installversion:" + installVersion); 
269	                boolean googlePlayInstantParam = installReferrer.getGooglePlayInstantParam(); 
270	                Log.v(ConstDefine.TAG, "instantExperienceLaunched:" + googlePlayInstantParam); 
271	            } catch (RemoteException e2) { 
272	                e2.printStackTrace(); 
273	            } 
274	        } 
275	    } 
276	 
277	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
278	    class i implements PermissionsUtils.IPermissionsResult { 
279	        i() { 
280	        } 
281	 
282	        @Override // org.cocos2dx.utils.PermissionsUtils.IPermissionsResult 
283	        public void forbitPermissons() { 
284	        } 
285	 
286	        @Override // org.cocos2dx.utils.PermissionsUtils.IPermissionsResult 
287	        public void passPermissons() { 
288	        } 
289	    } 
290	 
291	    /* JADX INFO: Access modifiers changed from: package-private */ 
292	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
293	    public class j extends Handler { 
294	        j(Looper looper) { 
295	            super(looper); 
296	        } 
297	 
298	        /* JADX WARN: Can't fix incorrect switch cases order, some code will duplicate */ 
299	        @Override // android.os.Handler 
300	        public void handleMessage(Message message) { 
301	            Intent intent; 
302	            AppActivity appActivity; 
303	            int i; 
304	            AdjustEvent adjustEvent; 
305	            String str; 
306	            AppActivity appActivity2; 
307	            int i2; 
308	            AppActivity appActivity3; 
309	            String str2; 
310	            Intent intent2; 
311	            ClipData primaryClip; 
312	            Bundle bundle; 
313	            com.facebook.f0.g gVar; 
314	            String str3; 
315	            Bundle bundle2; 
316	            com.facebook.f0.g gVar2; 
317	            String str4; 
318	            int i3 = message.what; 
319	            if (i3 != 1) { 
320	                if (i3 == 8) { 
321	                    ThirdParty.PLATFORM platform = ThirdParty.getInstance().getPlatform(message.arg1); 
322	                    if (platform != ThirdParty.PLATFORM.INVALIDPLAT) { 
323	                        ThirdParty.getInstance().thirdPartyLogin(platform, AppActivity.this.m_LoginListener); 
324	                        return; 
325	                    } 
326	                    return; 
327	                } else if (i3 == 12) { 
328	                    ThirdParty.getInstance().targetShare(AppActivity.this.m_ShareListener, (ThirdDefine.ShareParam) message.obj); 
329	                    return; 
330	                } else { 
331	                    if (i3 != 3007) { 
332	                        int i4 = 0; 
333	                        if (i3 == 9999) { 
334	                            int parseInt = Integer.parseInt((String) message.obj); 
335	                            if (parseInt == 1) { 
336	                                AppActivity.this.setRequestedOrientation(0); 
337	                                return; 
338	                            } else if (parseInt == 2) { 
339	                                AppActivity.this.setRequestedOrientation(1); 
340	                                return; 
341	                            } else if (parseInt == 3) { 
342	                                AppActivity.this.setRequestedOrientation(2); 
343	                                return; 
344	                            } else { 
345	                                return; 
346	                            } 
347	                        } 
348	                        String str5 = ""; 
349	                        if (i3 == 20100) { 
350	                            String str6 = (String) message.obj; 
351	                            if (str6 != "") { 
352	                                try { 
353	                                    ArrayList arrayList = new ArrayList(); 
354	                                    JSONObject jSONObject = new JSONObject(str6); 
355	                                    JSONArray jSONArray = jSONObject.getJSONArray("list"); 
356	                                    String string = jSONObject.getString("url"); 
357	                                    while (i4 < jSONArray.length()) { 
358	                                        arrayList.add(jSONArray.getString(i4)); 
359	                                        i4++; 
360	                                    } 
361	                                    for (PackageInfo packageInfo : AppActivity.this.getPackageManager().getInstalledPackages(8192)) { 
362	                                        packageInfo.applicationInfo.loadLabel(AppActivity.this.getPackageManager()).toString(); 
363	                                        packageInfo.applicationInfo.loadIcon(AppActivity.this.getPackageManager()); 
364	                                        String str7 = packageInfo.packageName; 
365	                                        if (arrayList.contains(str7)) { 
366	                                            Intent intent3 = new Intent(); 
367	                                            intent3.setAction("android.intent.action.VIEW"); 
368	                                            intent3.setData(Uri.parse(string)); 
369	                                            intent3.setPackage(str7); 
370	                                            AppActivity.this.startActivityForResult(intent3, 20100); 
371	                                            Log.i(ConstDefine.TAG, "getURLData ==> " + string); 
372	                                            return; 
373	                                        } 
374	                                    } 
375	                                    return; 
376	                                } catch (Exception e2) { 
377	                                    e2.printStackTrace(); 
378	                                    return; 
379	                                } 
380	                            } 
381	                            return; 
382	                        } 
383	                        if (i3 == 3) { 
384	                            str = (String) message.obj; 
385	                            appActivity2 = AppActivity.this; 
386	                            i2 = AppActivity.instance.m_nPickImgCallFunC; 
387	                        } else if (i3 != 4) { 
388	                            if (i3 == 5) { 
389	                                String str8 = (String) message.obj; 
390	                                if (str8 != null && "" != str8) { 
391	                                    ThirdParty.PLATFORM platform2 = ThirdParty.getInstance().getPlatform(message.arg1); 
392	                                    if (platform2 != ThirdParty.PLATFORM.INVALIDPLAT) { 
393	                                        ThirdParty.getInstance().configThirdParty(platform2, str8); 
394	                                        return; 
395	                                    } 
396	                                    return; 
397	                                } 
398	                                appActivity3 = AppActivity.this; 
399	                                str2 = "配置信息异常"; 
400	                            } else if (i3 == 2000) { 
401	                                str = (String) message.obj; 
402	                                if (str == null) { 
403	                                    return; 
404	                                } 
405	                                appActivity2 = AppActivity.this; 
406	                                i2 = appActivity2.m_nsetDragButton; 
407	                            } else if (i3 == 2001) { 
408	                                int i5 = 50; 
409	                                try { 
410	                                    JSONObject jSONObject2 = new JSONObject((String) message.obj); 
411	                                    str5 = jSONObject2.getString("filepath"); 
412	                                    i4 = jSONObject2.getInt("cloudMove"); 
413	                                    i5 = jSONObject2.getInt("width"); 
414	                                } catch (JSONException e3) { 
415	                                    e3.printStackTrace(); 
416	                                } 
417	                                AppActivity.this.setDrabuttonAndShow(BitmapFactory.decodeFile(str5), i4, i5); 
418	                                return; 
419	                            } else if (i3 == 4001) { 
420	                                String str9 = (String) message.obj; 
421	                                if (str9 != null) { 
422	                                    AdjustConfig adjustConfig = new AdjustConfig(AppActivity.instance, str9, AdjustConfig.ENVIRONMENT_PRODUCTION, true); 
423	                                    adjustConfig.setLogLevel(LogLevel.VERBOSE); 
424	                                    adjustConfig.setSendInBackground(true); 
425	                                    Adjust.onCreate(adjustConfig); 
426	                                    return; 
427	                                } 
428	                                return; 
429	                            } else if (i3 != 4002) { 
430	                                switch (i3) { 
431	                                    case 15: 
432	                                        intent = new Intent("android.intent.action.PICK", ContactsContract.Contacts.CONTENT_URI); 
433	                                        appActivity = AppActivity.this; 
434	                                        i = 1003; 
435	                                        break; 
436	                                    case 16: 
437	                                        String str10 = (String) message.obj; 
438	                                        if (str10 != "") { 
439	                                            intent2 = new Intent(); 
440	                                            intent2.setAction("android.intent.action.VIEW"); 
441	                                            intent2.setData(Uri.parse(str10)); 
442	                                            break; 
443	                                        } else { 
444	                                            return; 
445	                                        } 
446	                                    case 17: 
447	                                        String str11 = (String) message.obj; 
448	                                        ((ClipboardManager) AppActivity.this.getSystemService("clipboard")).setPrimaryClip(ClipData.newPlainText("txt copy", str11)); 
449	                                        if (!str11.equals("")) { 
450	                                            appActivity3 = AppActivity.this; 
451	                                            str2 = "Copy successfully!"; 
452	                                            break; 
453	                                        } else { 
454	                                            return; 
455	                                        } 
456	                                    default: 
457	                                        switch (i3) { 
458	                                            case 19: 
459	                                                ClipboardManager clipboardManager = (ClipboardManager) AppActivity.instance.getSystemService("clipboard"); 
460	                                                if (clipboardManager.hasPrimaryClip() && (primaryClip = clipboardManager.getPrimaryClip()) != null) { 
461	                                                    ClipData.Item itemAt = primaryClip.getItemAt(0); 
462	                                                    if (itemAt.getText() != null) { 
463	                                                        str5 = itemAt.getText().toString(); 
464	                                                    } 
465	                                                } 
466	                                                AppActivity appActivity4 = AppActivity.this; 
467	                                                appActivity4.toLuaFunC(appActivity4.m_nGetCopyDataFunC, str5); 
468	                                                Log.i(ConstDefine.TAG, "ClipboardManager ==> " + str5); 
469	                                                AppActivity.this.m_nGetCopyDataFunC = -1; 
470	                                                break; 
471	                                            case 20: 
472	                                                break; 
473	                                            case 21: 
474	                                                String str12 = (String) message.obj; 
475	                                                if (str12 == null || str12.trim().length() >= 0) { 
476	                                                    intent2 = new Intent("android.intent.action.DIAL", Uri.parse("tel:" + str12.trim())); 
477	                                                    break; 
478	                                                } else { 
479	                                                    return; 
480	                                                } 
481	                                            case 22: 
482	                                                int unused = AppActivity.m_nNetStatus = 3; 
483	                                                return; 
484	                                            case 23: 
485	                                                int unused2 = AppActivity.m_nNetStatus = 2; 
486	                                                return; 
487	                                            case 24: 
488	                                                int unused3 = AppActivity.m_nNetStatus = 1; 
489	                                                return; 
490	                                            default: 
491	                                                switch (i3) { 
492	                                                    case 3001: 
493	                                                        bundle = new Bundle(); 
494	                                                        bundle.putString("item_name", "Phone"); 
495	                                                        AppActivity.mFirebaseAnalytics.a("sign_up", bundle); 
496	                                                        gVar = AppActivity.this.logger; 
497	                                                        str3 = "fb_mobile_complete_registration"; 
498	                                                        gVar.g(str3, bundle); 
499	                                                        return; 
500	                                                    case 3002: 
501	                                                        String str13 = (String) message.obj; 
502	                                                        if (str13 != null) { 
503	                                                            int intValue = new Integer(str13).intValue(); 
504	                                                            Bundle bundle3 = new Bundle(); 
505	                                                            bundle3.putString("score", "" + intValue); 
506	                                                            bundle3.putString("CURRENCY", "INR"); 
507	                                                            bundle3.putString("quantity", "1"); 
508	                                                            bundle3.putString("price", "001"); 
509	                                                            bundle3.putString("order_id", "9999"); 
510	                                                            bundle3.putString("transaction_id", "9999"); 
511	                                                            AppActivity.mFirebaseAnalytics.a("purchase", bundle3); 
512	                                                            AppActivity.this.logger.h(new BigDecimal(intValue), Currency.getInstance("INR"), bundle3); 
513	                                                            return; 
514	                                                        } 
515	                                                        return; 
516	                                                    case 3003: 
517	                                                        String str14 = (String) message.obj; 
518	                                                        if (str14 != null) { 
519	                                                            int intValue2 = new Integer(str14).intValue(); 
520	                                                            bundle2 = new Bundle(); 
521	                                                            bundle2.putString("level", "" + intValue2); 
522	                                                            AppActivity.mFirebaseAnalytics.a("level_up", bundle2); 
523	                                                            gVar2 = AppActivity.this.logger; 
524	                                                            str4 = "fb_mobile_level_achieved"; 
525	                                                            gVar2.g(str4, bundle2); 
526	                                                            return; 
527	                                                        } 
528	                                                        return; 
529	                                                    case 3004: 
530	                                                        String str15 = (String) message.obj; 
531	                                                        if (str15 != null) { 
532	                                                            bundle2 = new Bundle(); 
533	                                                            bundle2.putString("success", "true"); 
534	                                                            bundle2.putString("game_id", str15); 
535	                                                            bundle2.putString("content", "Game Started"); 
536	                                                            AppActivity.mFirebaseAnalytics.a("tutorial_complete", bundle2); 
537	                                                            gVar2 = AppActivity.this.logger; 
538	                                                            str4 = "fb_mobile_tutorial_completion"; 
539	                                                            gVar2.g(str4, bundle2); 
540	                                                            return; 
541	                                                        } 
542	                                                        return; 
543	                                                    case 3005: 
544	                                                        Object obj = message.obj; 
545	                                                        String str16 = (String) obj; 
546	                                                        if (((String) obj) != null) { 
547	                                                            new HashMap(); 
548	                                                            bundle = new Bundle(); 
549	                                                            bundle.putString("content", "Good Game"); 
550	                                                            bundle.putString("platform", str16); 
551	                                                            str3 = "share"; 
552	                                                            AppActivity.mFirebaseAnalytics.a("share", bundle); 
553	                                                            gVar = AppActivity.this.logger; 
554	                                                            gVar.g(str3, bundle); 
555	                                                            return; 
556	                                                        } 
557	                                                        return; 
558	                                                    default: 
559	                                                        return; 
560	                                                } 
561	                                        } 
562	                                        String str17 = (String) message.obj; 
563	                                        if (str17 != null) { 
564	                                            AppActivity.this.toLuaGlobalFunC(AppActivity.g_LuaToastFun, str17); 
565	                                            return; 
566	                                        } 
567	                                        return; 
568	                                } 
569	                                AppActivity.this.startActivity(intent2); 
570	                                return; 
571	                            } else { 
572	                                String str18 = (String) message.obj; 
573	                                if (str18 == null) { 
574	                                    return; 
575	                                } 
576	                                adjustEvent = new AdjustEvent(str18); 
577	                            } 
578	                            appActivity3.toLuaToast(str2); 
579	                            return; 
580	                        } else { 
581	                            intent = new Intent("android.intent.action.PICK", (Uri) null); 
582	                            intent.setDataAndType(MediaStore.Images.Media.EXTERNAL_CONTENT_URI, "image/*"); 
583	                            appActivity = AppActivity.this; 
584	                            i = 1002; 
585	                        } 
586	                        appActivity2.toLuaFunC(i2, str); 
587	                        return; 
588	                    } 
589	                    Bundle bundle4 = new Bundle(); 
590	                    bundle4.putString("bouns_type", "coins"); 
591	                    AppActivity.mFirebaseAnalytics.a("bonus_claimed", bundle4); 
592	                    AppActivity.this.logger.g("bonus_claimed", bundle4); 
593	                    adjustEvent = new AdjustEvent(AppActivity.this.getString(2131623966)); 
594	                    Adjust.trackEvent(adjustEvent); 
595	                    return; 
596	                } 
597	            } 
598	            intent = new Intent("android.intent.action.PICK", (Uri) null); 
599	            intent.setDataAndType(MediaStore.Images.Media.EXTERNAL_CONTENT_URI, "image/*"); 
600	            appActivity = AppActivity.this; 
601	            i = 1000; 
602	            appActivity.startActivityForResult(intent, i); 
603	        } 
604	    } 
605	 
606	    /* JADX INFO: Access modifiers changed from: package-private */ 
607	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
608	    public class k implements ThirdParty.OnLoginListener { 
609	        k() { 
610	        } 
611	 
612	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnLoginListener 
613	        public void onLoginCancel(ThirdParty.PLATFORM platform, String str) { 
614	            AppActivity appActivity = AppActivity.this; 
615	            appActivity.toLuaFunC(appActivity.m_nThirdLoginFunC, str); 
616	            AppActivity.this.m_nThirdLoginFunC = -1; 
617	        } 
618	 
619	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnLoginListener 
620	        public void onLoginFail(ThirdParty.PLATFORM platform, String str) { 
621	            AppActivity appActivity = AppActivity.this; 
622	            appActivity.toLuaFunC(appActivity.m_nThirdLoginFunC, str); 
623	            AppActivity.this.m_nThirdLoginFunC = -1; 
624	        } 
625	 
626	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnLoginListener 
627	        public void onLoginStart(ThirdParty.PLATFORM platform, String str) { 
628	        } 
629	 
630	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnLoginListener 
631	        public void onLoginSuccess(ThirdParty.PLATFORM platform, String str) { 
632	            AppActivity appActivity = AppActivity.this; 
633	            appActivity.toLuaFunC(appActivity.m_nThirdLoginFunC, str); 
634	            AppActivity.this.m_nThirdLoginFunC = -1; 
635	        } 
636	    } 
637	 
638	    /* JADX INFO: Access modifiers changed from: package-private */ 
639	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/3.dex */ 
640	    public class l implements ThirdParty.OnShareListener { 
641	        l() { 
642	        } 
643	 
644	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnShareListener 
645	        public void onCancel(ThirdParty.PLATFORM platform) { 
646	            AppActivity appActivity = AppActivity.this; 
647	            appActivity.toLuaFunC(appActivity.m_nShareFunC, "false"); 
648	            AppActivity.this.m_nShareFunC = -1; 
649	        } 
650	 
651	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnShareListener 
652	        public void onComplete(ThirdParty.PLATFORM platform, int i, String str) { 
653	            AppActivity appActivity = AppActivity.this; 
654	            appActivity.toLuaFunC(appActivity.m_nShareFunC, "true"); 
655	            AppActivity.this.m_nShareFunC = -1; 
656	        } 
657	 
658	        @Override // org.cocos2dx.thirdparty.ThirdParty.OnShareListener 
659	        public void onError(ThirdParty.PLATFORM platform, String str) { 
660	            AppActivity appActivity = AppActivity.this; 
661	            appActivity.toLuaFunC(appActivity.m_nShareFunC, "false"); 
662	            AppActivity.this.m_nShareFunC = -1; 
663	        } 
664	    } 
665	 
666	    /* JADX INFO: Access modifiers changed from: package-private */ 
667	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
668	    public class m implements Runnable { 
669	        final /* synthetic */ int j; 
670	        final /* synthetic */ String k; 
671	 
672	        m(int i, String str) { 
673	            this.j = i; 
674	            this.k = str; 
675	        } 
676	 
677	        @Override // java.lang.Runnable 
678	        public void run() { 
679	            Cocos2dxLuaJavaBridge.callLuaFunctionWithString(this.j, this.k); 
680	            Cocos2dxLuaJavaBridge.releaseLuaFunction(this.j); 
681	        } 
682	    } 
683	 
684	    /* loaded from: /storage/emulated/0/Documents/jadec/sources/com.rummyolaJRFJUN.rummyola.qp/dex-files/2.dex */ 
685	    private class n extends PhoneStateListener { 
686	        private n() { 
687	        } 
688	 
689	        /* synthetic */ n(AppActivity appActivity, e eVar) { 
690	            this(); 
691	        } 
692	 
693	        @Override // android.telephony.PhoneStateListener 
694	        public void onSignalStrengthsChanged(SignalStrength signalStrength) { 
695	            Message message; 
696	            int i; 
697	            super.onSignalStrengthsChanged(signalStrength); 
698	            int gsmSignalStrength = signalStrength.getGsmSignalStrength(); 
699	            Log.d(ConstDefine.TAG, "PhoneStatListener------ gsm signal --> " + gsmSignalStrength); 
700	            if (gsmSignalStrength <= 30) { 
701	                if (gsmSignalStrength > 20 && gsmSignalStrength < 30) { 
702	                    message = new Message(); 
703	                } else if (gsmSignalStrength < 20 && gsmSignalStrength > 3) { 
704	                    message = new Message(); 
705	                } else if (gsmSignalStrength >= 3) { 
706	                    return; 
707	                } else { 
708	                    message = new Message(); 
709	                    i = 24; 
710	                } 
711	                message.what = 23; 
712	                AppActivity.this.m_hHandler.sendMessage(message); 
713	            } 
714	            message = new Message(); 
715	            i = 22; 
716	            message.what = i; 
717	            AppActivity.this.m_hHandler.sendMessage(message); 
718	        } 
719	    } 
720	 
721	    public static void GetServerInfo(String str, int i2, int i3) { 
722	        Message obtain = Message.obtain(); 
723	        obtain.what = ThirdDefine.THIRD_PER_REQUEST; 
724	        obtain.obj = str + ":" + i2; 
725	        obtain.arg1 = i3; 
726	        instance.sendMessageWith(obtain); 
727	    } 
728	 
729	    public static void cancelRecord() { 
730	        MP3Recorder mP3Recorder = recorder; 
731	        if (mP3Recorder != null) { 
732	            mP3Recorder.cancel(); 
733	        } 
734	    } 
735	 
736	    @SuppressLint({"Range"}) 
737	    private void contactPickEnd(Uri uri) { 
738	        String str; 
739	        String str2; 
740	        ContentResolver contentResolver = getContentResolver(); 
741	        Cursor query = contentResolver.query(uri, null, null, null, null); 
742	        String str3 = ""; 
743	        if (query != null) { 
744	            query.moveToFirst(); 
745	            str2 = query.getString(query.getColumnIndex("display_name")); 
746	            String string = query.getString(query.getColumnIndex("_id")); 
747	            Uri uri2 = ContactsContract.CommonDataKinds.Phone.CONTENT_URI; 
748	            Cursor query2 = contentResolver.query(uri2, null, "contact_id=" + string, null, null); 
749	            if (query2 != null) { 
750	                try { 
751	                } catch (Exception e2) { 
752	                    e2.printStackTrace(); 
753	                } 
754	                if (query2.getColumnIndex("data1") > 0) { 
755	                    query2.moveToFirst(); 
756	                    str = query2.getString(query2.getColumnIndex("data1")); 
757	                    query2.close(); 
758	                    query.close(); 
759	                } 
760	            } 
761	            str = ""; 
762	            query2.close(); 
763	            query.close(); 
764	        } else { 
765	            str = ""; 
766	            str2 = str; 
767	        } 
768	        JSONObject jSONObject = new JSONObject(); 
769	        try { 
770	            jSONObject.put("contactName", str2); 
771	            jSONObject.put("contactNumber", str); 
772	            str3 = jSONObject.toString(); 
773	        } catch (JSONException e3) { 
774	            e3.printStackTrace(); 
775	        } 
776	        toLuaFunC(this.m_nContactFunC, str3); 
777	        this.m_nContactFunC = -1; 
778	    } 
779	 
780	    public static boolean copyToClipboard(String str) { 
781	        Log.d(ConstDefine.TAG, "复制到剪贴板:" + str); 
782	        Message obtain = Message.obtain(); 
783	        obtain.what = 17; 
784	        obtain.obj = str; 
785	        instance.sendMessageWith(obtain); 
786	        return true; 
787	    } 
788	 
789	    public static void deleteThirdPartyAuthorization(int i2, int i3) { 
790	        instance.m_nDelAuthorizationFunC = i3; 
791	        Message obtain = Message.obtain(); 
792	        obtain.what = 18; 
793	        obtain.arg1 = i2; 
794	        instance.sendMessageWith(obtain); 
795	    } 
796	 
797	    public static int getBatteryLevel() { 
798	        return m_nBatteryLevel; 
799	    } 
800	 
801	    public static String getClientPackageName() { 
802	        try { 
803	            return instance.getPackageName(); 
804	        } catch (Exception unused) { 
805	            return ""; 
806	        } 
807	    } 
808	 
809	    public static Context getContext() { 
810	        return STATIC_REF; 
811	    } 
812	 
813	    public static void getCopyBoardData(int i2) { 
814	        instance.m_nGetCopyDataFunC = i2; 
815	        Message obtain = Message.obtain(); 
816	        obtain.what = 19; 
817	        instance.sendMessageWith(obtain); 
818	    } 
819	 
820	    public static String getDeviceToken() { 
821	        return instance.m_szDeviceToken; 
822	    } 
823	 
824	    private IntentFilter getFilter() { 
825	        IntentFilter intentFilter = new IntentFilter(); 
826	        intentFilter.addAction("android.intent.action.BATTERY_CHANGED"); 
827	        return intentFilter; 
828	    } 
829	 
830	    public static String getHostAdress() { 
831	        return Utils.getHostIpAddress(instance); 
832	    } 
833	 
834	    public static String getLaunchData() { 
835	        AppActivity appActivity = instance; 
836	        String str = appActivity.m_szLaunchData; 
837	        appActivity.m_szLaunchData = ""; 
838	        return str; 
839	    } 
840	 
841	    public static String getLocalIpAddress() { 
842	        return hostIPAdress; 
843	    } 
844	 
845	    public static String getNation() { 
846	        return UserNation; 
847	    } 
848	 
849	    public static int getNetWorkType(Context context) { 
850	        NetworkInfo activeNetworkInfo = ((ConnectivityManager) context.getSystemService("connectivity")).getActiveNetworkInfo(); 
851	        if (activeNetworkInfo == null || !activeNetworkInfo.isConnected()) { 
852	            return 0; 
853	        } 
854	        String typeName = activeNetworkInfo.getTypeName(); 
855	        if (typeName.equalsIgnoreCase("WIFI")) { 
856	            return 1; 
857	        } 
858	        return typeName.equalsIgnoreCase("MOBILE") ? 2 : -1; 
859	    } 
860	 
861	    public static String getSDCardDocPath() { 
862	        Log.i(ConstDefine.TAG, "getSDCardDocPath tag " + Utils.getSDCardDocPath(instance)); 
863	        return Utils.getSDCardDocPath(instance); 
864	    } 
865	 
866	    public static void getSelfClient(int i2) { 
867	        Log.d(ConstDefine.TAG, "getSelfClient"); 
868	        Message obtain = Message.obtain(); 
869	        obtain.what = 10002; 
870	        obtain.arg1 = i2; 
871	        instance.sendMessageWith(obtain); 
872	    } 
873	 
874	    public static String getStringStatus() { 
875	        return stringStatus; 
876	    } 
877	 
878	    public static String getStringType() { 
879	        return stringType; 
880	    } 
881	 
882	    private void getURLData() { 
883	        Uri data; 
884	        Intent intent = getIntent(); 
885	        if (intent == null || !"android.intent.action.VIEW".equals(intent.getAction()) || (data = intent.getData()) == null) { 
886	            return; 
887	        } 
888	        String query = data.getQuery(); 
889	        Log.i(ConstDefine.TAG, "getURLData ==> " + query); 
890	        this.m_szLaunchData = query; 
891	    } 
892	 
893	    public static String getUUID() { 
894	        return Utils.getDeviceUUID(instance); 
895	    } 
896	 
897	    public static String getUserAdid() { 
898	        Log.d(ConstDefine.TAG, "getUserAdid:" + sdfsdg); 
899	        return sdfsdg; 
900	    } 
901	 
902	    public static int getWIFIStatus() { 
903	        return m_nNetStatus; 
904	    } 
905	 
906	    public static void goToSetting() { 
907	        instance.startActivity(new Intent("android.settings.SETTINGS")); 
908	    } 
909	 
910	    public static void goToWeChat() { 
911	        Intent intent = new Intent(); 
912	        ComponentName componentName = new ComponentName("com.tencent.mm", "com.tencent.mm.ui.LauncherUI"); 
913	        intent.setAction("android.intent.action.MAIN"); 
914	        intent.addCategory("android.intent.category.LAUNCHER"); 
915	        intent.addFlags(268435456); 
916	        intent.setComponent(componentName); 
917	        instance.startActivity(intent); 
918	    } 
919	 
920	    /* JADX INFO: Access modifiers changed from: private */ 
921	    public void hideNavigationBarDDD() { 
922	        getWindow().getDecorView().setSystemUiVisibility(Build.VERSION.SDK_INT >= 19 ? 5894 : 1799); 
923	    } 
924	 
925	    private void initHandlersss() { 
926	        this.m_hHandler = new j(Looper.getMainLooper()); 
927	    } 
928	 
929	    private void initLoginListener() { 
930	        this.m_LoginListener = new k(); 
931	    } 
932	 
933	    private void initShareListener() { 
934	        this.m_ShareListener = new l(); 
935	    } 
936	 
937	    public static void initWithKeyAndID(String str, String str2, int i2) { 
938	        Message obtain = Message.obtain(); 
939	        obtain.what = 10000; 
940	        obtain.obj = str + ":" + str2; 
941	        obtain.arg1 = i2; 
942	        instance.sendMessageWith(obtain); 
943	    } 
944	 
945	    public static void installClient(String str) { 
946	        if ("".equals(str)) { 
947	            return; 
948	        } 
949	        File file = new File(str); 
950	        if (file.exists()) { 
951	            Intent intent = new Intent("android.intent.action.VIEW"); 
952	            intent.setDataAndType(Uri.fromFile(file), "application/vnd.android.package-archive"); 
953	            instance.startActivity(intent); 
954	        } 
955	    } 
956	 
957	    public static boolean isHaveRecordPermission() { 
958	        PackageManager packageManager = instance.getPackageManager(); 
959	        Log.i(ConstDefine.TAG, "Permission pstate ==> " + packageManager.checkPermission("android.permission.RECORD_AUDIO", instance.getPackageName())); 
960	        return packageManager.checkPermission("android.permission.RECORD_AUDIO", instance.getPackageName()) == 0; 
961	    } 
962	 
963	    public static boolean isNetworkAvailable() { 
964	        return Utils.isNetworkAvailable(instance); 
965	    } 
966	 
967	    private boolean isNetworkConnected() { 
968	        return Utils.isNetworkConnected(this); 
969	    } 
970	 
971	    private static native boolean nativeIsDebug(); 
972	 
973	    private static native boolean nativeIsLandScape(); 
974	 
975	    public static native void nativeLogData(String str); 
976	 
977	    public static void onAdjustEventClick(String str) { 
978	        Log.d(ConstDefine.TAG, "adjustEvent:" + str); 
979	        Message obtain = Message.obtain(); 
980	        obtain.what = 4002; 
981	        obtain.obj = str; 
982	        instance.sendMessageWith(obtain); 
983	    } 
984	 
985	    public static void onBouns() { 
986	        Log.d(ConstDefine.TAG, "onBouns"); 
987	        Message obtain = Message.obtain(); 
988	        obtain.what = 3007; 
989	        instance.sendMessageWith(obtain); 
990	    } 
991	 
992	    public static void onDescription(String str) { 
993	        Log.d(ConstDefine.TAG, "onDescription:" + str); 
994	        Message obtain = Message.obtain(); 
995	        obtain.what = 3005; 
996	        obtain.obj = str; 
997	        instance.sendMessageWith(obtain); 
998	    } 
999	 
1000	    public static void onFacebookLogon(int i2) { 
1001	        Log.d(ConstDefine.TAG, "onFacebookLogon"); 
1002	        Message obtain = Message.obtain(); 
1003	        obtain.what = 20000; 
1004	        obtain.arg1 = i2; 
1005	        instance.sendMessageWith(obtain); 
1006	    } 
1007	 
1008	    public static void onGetLevel(String str) { 
1009	        Log.d(ConstDefine.TAG, "onGetLevel:" + str); 
1010	        Message obtain = Message.obtain(); 
1011	        obtain.what = 3003; 
1012	        obtain.obj = str; 
1013	        instance.sendMessageWith(obtain); 
1014	    } 
1015	 
1016	    public static void onLogin() { 
1017	        Log.d(ConstDefine.TAG, "onLogin"); 
1018	        Message obtain = Message.obtain(); 
1019	        obtain.what = 3000; 
1020	        instance.sendMessageWith(obtain); 
1021	    } 
1022	 
1023	    public static void onPlayGame(String str) { 
1024	        Log.d(ConstDefine.TAG, "onPlayGame:" + str); 
1025	        Message obtain = Message.obtain(); 
1026	        obtain.what = 3004; 
1027	        obtain.obj = str; 
1028	        instance.sendMessageWith(obtain); 
1029	    } 
1030	 
1031	    public static void onRegistration() { 
1032	        Log.d(ConstDefine.TAG, "onRegistration"); 
1033	        Message obtain = Message.obtain(); 
1034	        obtain.what = 3001; 
1035	        instance.sendMessageWith(obtain); 
1036	    } 
1037	 
1038	    public static void onRevenue(String str) { 
1039	        Log.d(ConstDefine.TAG, "onRevenue:" + str); 
1040	        Message obtain = Message.obtain(); 
1041	        obtain.what = 3002; 
1042	        obtain.obj = str; 
1043	        instance.sendMessageWith(obtain); 
1044	    } 
1045	 
1046	    public static void openBrowser(String str) { 
1047	        Log.d(ConstDefine.TAG, "启动浏览器:" + str); 
1048	        Message obtain = Message.obtain(); 
1049	        obtain.what = 16; 
1050	        obtain.obj = str; 
1051	        instance.sendMessageWith(obtain); 
1052	    } 
1053	 
1054	    /* JADX WARN: Code restructure failed: missing block: B:33:0x00eb, code lost: 
1055	        r2.put("client_id", r11.getString("client_id")); 
1056	     */ 
1057	    /* 
1058	        Code decompiled incorrectly, please refer to instructions dump. 
1059	        To view partially-correct code enable 'Show inconsistent code' option in preferences 
1060	    */ 
1061	    public static java.util.Map<java.lang.String, java.lang.String> parse(java.lang.String r10, java.lang.String r11) { 
1062	        /* 
1063	            Method dump skipped, instructions count: 258 
1064	            To view this dump change 'Code comments level' option to 'DEBUG' 
1065	        */ 
1066	        throw new UnsupportedOperationException("Method not decompiled: org.cocos2dx.lua.AppActivity.parse(java.lang.String, java.lang.String):java.util.Map"); 
1067	    } 
1068	 
1069	    private void photoClipEnd(Bundle bundle) { 
1070	        Log.v("photo", "clip end"); 
1071	        if (bundle != null) { 
1072	            Bitmap bitmap = (Bitmap) bundle.getParcelable("data"); 
1073	            try { 
1074	                String str = "/@ci_" + getPackageName() + ".png"; 
1075	                String path = getFilesDir().getPath(); 
1076	                String str2 = path + str; 
1077	                BufferedOutputStream bufferedOutputStream = new BufferedOutputStream(new FileOutputStream(new File(path, str))); 
1078	                bitmap.compress(Bitmap.CompressFormat.PNG, 100, bufferedOutputStream); 
1079	                bufferedOutputStream.flush(); 
1080	                bufferedOutputStream.close(); 
1081	                sendMessageWithObj(3, str2); 
1082	            } catch (Exception e2) { 
1083	                e2.printStackTrace(); 
1084	                Log.e(ConstDefine.TAG, "Head 保存头像错误"); 
1085	            } 
1086	        } 
1087	    } 
1088	 
1089	    private void photoClipZIP(Uri uri) { 
1090	        Log.v("photo", "clip start"); 
1091	        Intent intent = new Intent("com.android.camera.action.CROP"); 
1092	        intent.setDataAndType(uri, "image/*"); 
1093	        intent.putExtra("crop", "true"); 
1094	        intent.putExtra("aspectX", 1); 
1095	        intent.putExtra("aspectY", 1); 
1096	        intent.putExtra("outputX", 96); 
1097	        intent.putExtra("outputY", 96); 
1098	        intent.putExtra("return-data", true); 
1099	        startActivityForResult(intent, 1001); 
1100	    } 
1101	 
1102	    private void photoPickEndwer(Uri uri) { 
1103	        Cursor managedQuery = managedQuery(uri, new String[]{"_data"}, null, null, null); 
1104	        int columnIndexOrThrow = managedQuery.getColumnIndexOrThrow("_data"); 
1105	        managedQuery.moveToFirst(); 
1106	        String string = managedQuery.getString(columnIndexOrThrow); 
1107	        Log.i(ConstDefine.TAG, "path " + string); 
1108	        toLuaFunC(this.m_nPickImgCallFunC, string); 
1109	        this.m_nPickImgCallFunC = -1; 
1110	    } 
1111	 
1112	    public static void pickImg(int i2, boolean z) { 
1113	        AppActivity appActivity = instance; 
1114	        appActivity.m_nPickImgCallFunC = i2; 
1115	        appActivity.sendMessage(z ? 1 : 4); 
1116	    } 
1117	 
1118	    /* JADX WARN: Removed duplicated region for block: B:17:0x0049  */ 
1119	    /* JADX WARN: Removed duplicated region for block: B:19:0x004f  */ 
1120	    /* 
1121	        Code decompiled incorrectly, please refer to instructions dump. 
1122	        To view partially-correct code enable 'Show inconsistent code' option in preferences 
1123	    */ 
1124	    public static java.util.Map<java.lang.String, java.lang.String> readJsonFile(android.content.Context r6) { 
1125	        /* 
1126	            r0 = 0 
1127	            android.content.res.Resources r1 = r6.getResources()     // Catch: java.lang.Exception -> L3b 
1128	            android.content.res.AssetManager r1 = r1.getAssets()     // Catch: java.lang.Exception -> L3b 
1129	            java.lang.String r2 = "base/res/google-services.json" 
1130	            java.io.InputStream r1 = r1.open(r2)     // Catch: java.lang.Exception -> L3b 
1131	            java.io.ByteArrayOutputStream r2 = new java.io.ByteArrayOutputStream     // Catch: java.lang.Exception -> L3b 
1132	            r2.<init>()     // Catch: java.lang.Exception -> L3b 
1133	            r3 = 1024(0x400, float:1.435E-42) 
1134	            byte[] r3 = new byte[r3]     // Catch: java.lang.Exception -> L3b 
1135	        L18: 
1136	            int r4 = r1.read(r3)     // Catch: java.lang.Exception -> L3b 
1137	            r5 = -1 
1138	            if (r4 == r5) goto L24 
1139	            r5 = 0 
1140	            r2.write(r3, r5, r4)     // Catch: java.lang.Exception -> L3b 
1141	            goto L18 
1142	        L24: 
1143	            r2.flush()     // Catch: java.lang.Exception -> L3b 
1144	            java.lang.String r3 = new java.lang.String     // Catch: java.lang.Exception -> L3b 
1145	            byte[] r4 = r2.toByteArray()     // Catch: java.lang.Exception -> L3b 
1146	            java.lang.String r5 = "ISO-8859-1" 
1147	            r3.<init>(r4, r5)     // Catch: java.lang.Exception -> L3b 
1148	            r2.close()     // Catch: java.lang.Exception -> L39 
1149	            r1.close()     // Catch: java.lang.Exception -> L39 
1150	            goto L40 
1151	        L39: 
1152	            r1 = move-exception 
1153	            goto L3d 
1154	        L3b: 
1155	            r1 = move-exception 
1156	            r3 = r0 
1157	        L3d: 
1158	            r1.printStackTrace() 
1159	        L40: 
1160	            java.lang.String r1 = "MyTest" 
1161	            java.lang.String r2 = "FirebaseAnalytics初始化 成功2" 
1162	            android.util.Log.v(r1, r2) 
1163	            if (r3 != 0) goto L4f 
1164	            java.lang.String r6 = "FirebaseAnalytics初始化 成功3" 
1165	            android.util.Log.v(r1, r6) 
1166	            return r0 
1167	        L4f: 
1168	            java.lang.String r6 = r6.getPackageName() 
1169	            java.util.Map r6 = parse(r3, r6) 
1170	            return r6 
1171	        */ 
1172	        throw new UnsupportedOperationException("Method not decompiled: org.cocos2dx.lua.AppActivity.readJsonFile(android.content.Context):java.util.Map"); 
1173	    } 
1174	 
1175	    public static String referrerUrl() { 
1176	        return referrerUrl; 
1177	    } 
1178	 
1179	    public static void requestContact(int i2) { 
1180	        instance.m_nContactFunC = i2; 
1181	        Message obtain = Message.obtain(); 
1182	        obtain.what = 15; 
1183	        instance.sendMessageWith(obtain); 
1184	    } 
1185	 
1186	    public static void requestLocation(int i2) { 
1187	        instance.m_nLocationFunC = i2; 
1188	        Message obtain = Message.obtain(); 
1189	        obtain.what = 14; 
1190	        instance.sendMessageWith(obtain); 
1191	    } 
1192	 
1193	    public static boolean saveImgToSystemGallery(String str, String str2) { 
1194	        try { 
1195	            MediaStore.Images.Media.insertImage(instance.getContentResolver(), str, str2, (String) null); 
1196	            AppActivity appActivity = instance; 
1197	            appActivity.sendBroadcast(new Intent("android.intent.action.MEDIA_SCANNER_SCAN_FILE", Uri.parse("file://" + str))); 
1198	            return true; 
1199	        } catch (FileNotFoundException e2) { 
1200	            e2.printStackTrace(); 
1201	            return false; 
1202	        } 
1203	    } 
1204	 
1205	    public static void schemeGo(String str) { 
1206	        Log.d(ConstDefine.TAG, "schemeGo"); 
1207	        Message obtain = Message.obtain(); 
1208	        obtain.what = 20100; 
1209	        obtain.obj = str; 
1210	        instance.sendMessageWith(obtain); 
1211	    } 
1212	 
1213	    public static void setAdjustidEvent(String str) { 
1214	        Log.d(ConstDefine.TAG, "adjustID:" + str); 
1215	        Message obtain = Message.obtain(); 
1216	        obtain.what = 4001; 
1217	        obtain.obj = str; 
1218	        instance.sendMessageWith(obtain); 
1219	    } 
1220	 
1221	    public static void setDragButtonAndCallBack(String str, int i2) { 
1222	        instance.m_nsetDragButton = i2; 
1223	        Message obtain = Message.obtain(); 
1224	        obtain.what = ConstDefine.DragFloatAction_Show; 
1225	        obtain.obj = str; 
1226	        instance.sendMessageWith(obtain); 
1227	        try { 
1228	            instance.m_alertJson = new JSONObject(str); 
1229	        } catch (JSONException e2) { 
1230	            e2.printStackTrace(); 
1231	        } 
1232	        Log.i(ConstDefine.TAG, "DragButton 设置图片以及回调"); 
1233	    } 
1234	 
1235	    public static void setScreenOrientation(String str) { 
1236	        Log.d(ConstDefine.TAG, "设置屏幕方向:" + str); 
1237	        Message obtain = Message.obtain(); 
1238	        obtain.what = 9999; 
1239	        obtain.obj = str; 
1240	        instance.sendMessageWith(obtain); 
1241	    } 
1242	 
1243	    public static void setTimesout(String str, String str2, int i2) { 
1244	        Log.d(ConstDefine.TAG, "setTimesout"); 
1245	        Message obtain = Message.obtain(); 
1246	        obtain.what = 10003; 
1247	        obtain.obj = str + "=" + str2; 
1248	        obtain.arg1 = i2; 
1249	        instance.sendMessageWith(obtain); 
1250	    } 
1251	 
1252	    public static void shareToTarget(int i2, String str, String str2, String str3, String str4, String str5, int i3) { 
1253	        ThirdDefine.ShareParam shareParam = new ThirdDefine.ShareParam(); 
1254	        shareParam.nTarget = i2; 
1255	        shareParam.sTitle = str; 
1256	        shareParam.sContent = str2; 
1257	        shareParam.sTargetURL = str3; 
1258	        shareParam.sMedia = str4; 
1259	        if (str5.equals("true")) { 
1260	            shareParam.bImageOnly = true; 
1261	        } 
1262	        AppActivity appActivity = instance; 
1263	        appActivity.m_nShareFunC = i3; 
1264	        appActivity.sendMessageWithObj(12, shareParam); 
1265	    } 
1266	 
1267	    public static void startRecord(String str) { 
1268	        Log.d(ConstDefine.TAG, "startRecord:" + str); 
1269	        if (recorder == null) { 
1270	            MP3Recorder mP3Recorder = new MP3Recorder(str, 44100); 
1271	            recorder = mP3Recorder; 
1272	            mP3Recorder.init(); 
1273	        } 
1274	        recorder.start(instance); 
1275	    } 
1276	 
1277	    public static void stopRecord() { 
1278	        MP3Recorder mP3Recorder = recorder; 
1279	        if (mP3Recorder != null) { 
1280	            mP3Recorder.stop(); 
1281	        } 
1282	    } 
1283	 
1284	    public static void systemCall(String str) { 
1285	        Log.d(ConstDefine.TAG, "拨号:" + str); 
1286	        Message obtain = Message.obtain(); 
1287	        obtain.what = 21; 
1288	        obtain.obj = str; 
1289	        instance.sendMessageWith(obtain); 
1290	    } 
1291	 
1292	    public static void testRecordService() { 
1293	        AudioRecord audioRecord = new AudioRecord(1, 44100, 16, 2, AudioRecord.getMinBufferSize(44100, 16, 2) * 2); 
1294	        try { 
1295	            try { 
1296	                Log.i(ConstDefine.TAG, " testRecordService start test"); 
1297	                audioRecord.startRecording(); 
1298	            } catch (IllegalStateException unused) { 
1299	                Log.i(ConstDefine.TAG, " testRecordService illegal stop"); 
1300	                audioRecord.release(); 
1301	                Log.i(ConstDefine.TAG, " testRecordService stop test"); 
1302	                throw null; 
1303	            } 
1304	        } finally { 
1305	            Log.i(ConstDefine.TAG, " testRecordService stop test"); 
1306	            audioRecord.stop(); 
1307	            audioRecord.release(); 
1308	        } 
1309	    } 
1310	 
1311	    public static void thirdLogin(int i2, int i3) { 
1312	        Message obtain = Message.obtain(); 
1313	        obtain.what = 8; 
1314	        obtain.arg1 = i2; 
1315	        AppActivity appActivity = instance; 
1316	        appActivity.m_nThirdLoginFunC = i3; 
1317	        appActivity.sendMessageWith(obtain); 
1318	    } 
1319	 
1320	    public static void thirdPartyConfig(int i2, String str) { 
1321	        Message obtain = Message.obtain(); 
1322	        obtain.what = 5; 
1323	        obtain.arg1 = i2; 
1324	        obtain.obj = str; 
1325	        instance.sendMessageWith(obtain); 
1326	    } 
1327	 
1328	    /* JADX INFO: Access modifiers changed from: private */ 
1329	    public void toLuaToast(String str) { 
1330	        Message obtain = Message.obtain(); 
1331	        obtain.what = 20; 
1332	        obtain.obj = str; 
1333	        this.m_hHandler.sendMessageDelayed(obtain, 500L); 
1334	    } 
1335	 
1336	    public static void userChannel(String str) { 
1337	        Log.d(ConstDefine.TAG, "userChannel:" + str); 
1338	        Message obtain = Message.obtain(); 
1339	        obtain.what = 3008; 
1340	        obtain.obj = str; 
1341	        instance.sendMessageWith(obtain); 
1342	    } 
1343	 
1344	    /* JADX WARN: Removed duplicated region for block: B:24:0x0050  */ 
1345	    /* JADX WARN: Removed duplicated region for block: B:26:0x0073  */ 
1346	    @Override // org.cocos2dx.lib.Cocos2dxActivity 
1347	    /* 
1348	        Code decompiled incorrectly, please refer to instructions dump. 
1349	        To view partially-correct code enable 'Show inconsistent code' option in preferences 
1350	    */ 
1351	    public void backButtonClick() { 
1352	        /* 
1353	            r8 = this; 
1354	            java.lang.String r0 = "" 
1355	            org.cocos2dx.lua.AppActivity r1 = org.cocos2dx.lua.AppActivity.instance 
1356	            org.json.JSONObject r1 = r1.m_alertJson 
1357	            java.lang.String r2 = "MyTest" 
1358	            if (r1 != 0) goto L10 
1359	            java.lang.String r0 = "DragButton instance.m_alertJson是空的" 
1360	            android.util.Log.i(r2, r0) 
1361	            return 
1362	        L10: 
1363	            r3 = 0 
1364	            java.lang.String r4 = "isShowAlert" 
1365	            int r3 = r1.getInt(r4)     // Catch: org.json.JSONException -> L46 
1366	            org.cocos2dx.lua.AppActivity r1 = org.cocos2dx.lua.AppActivity.instance     // Catch: org.json.JSONException -> L46 
1367	            org.json.JSONObject r1 = r1.m_alertJson     // Catch: org.json.JSONException -> L46 
1368	            java.lang.String r4 = "titleString" 
1369	            java.lang.String r1 = r1.getString(r4)     // Catch: org.json.JSONException -> L46 
1370	            org.cocos2dx.lua.AppActivity r4 = org.cocos2dx.lua.AppActivity.instance     // Catch: org.json.JSONException -> L43 
1371	            org.json.JSONObject r4 = r4.m_alertJson     // Catch: org.json.JSONException -> L43 
1372	            java.lang.String r5 = "contentString" 
1373	            java.lang.String r4 = r4.getString(r5)     // Catch: org.json.JSONException -> L43 
1374	            org.cocos2dx.lua.AppActivity r5 = org.cocos2dx.lua.AppActivity.instance     // Catch: org.json.JSONException -> L40 
1375	            org.json.JSONObject r5 = r5.m_alertJson     // Catch: org.json.JSONException -> L40 
1376	            java.lang.String r6 = "sureString" 
1377	            java.lang.String r5 = r5.getString(r6)     // Catch: org.json.JSONException -> L40 
1378	            org.json.JSONObject r6 = r8.m_alertJson     // Catch: org.json.JSONException -> L3e 
1379	            java.lang.String r7 = "cancleString" 
1380	            java.lang.String r0 = r6.getString(r7)     // Catch: org.json.JSONException -> L3e 
1381	            goto L4d 
1382	        L3e: 
1383	            r6 = move-exception 
1384	            goto L4a 
1385	        L40: 
1386	            r6 = move-exception 
1387	            r5 = r0 
1388	            goto L4a 
1389	        L43: 
1390	            r6 = move-exception 
1391	            r4 = r0 
1392	            goto L49 
1393	        L46: 
1394	            r6 = move-exception 
1395	            r1 = r0 
1396	            r4 = r1 
1397	        L49: 
1398	            r5 = r4 
1399	        L4a: 
1400	            r6.printStackTrace() 
1401	        L4d: 
1402	            r6 = 1 
1403	            if (r3 != r6) goto L73 
1404	            android.app.AlertDialog$Builder r2 = new android.app.AlertDialog$Builder 
1405	            r2.<init>(r8) 
1406	            r2.setTitle(r1) 
1407	            r2.setMessage(r4) 
1408	            org.cocos2dx.lua.AppActivity$b r1 = new org.cocos2dx.lua.AppActivity$b 
1409	            r1.<init>() 
1410	            r2.setPositiveButton(r5, r1) 
1411	            org.cocos2dx.lua.AppActivity$c r1 = new org.cocos2dx.lua.AppActivity$c 
1412	            r1.<init>() 
1413	            r2.setNegativeButton(r0, r1) 
1414	            android.app.AlertDialog r0 = r2.create() 
1415	            r0.show() 
1416	            return 
1417	        L73: 
1418	            java.lang.String r0 = "DragButton 按钮点击方法的重写" 
1419	            android.util.Log.i(r2, r0) 
1420	            android.os.Message r0 = android.os.Message.obtain() 
1421	            r1 = 2000(0x7d0, float:2.803E-42) 
1422	            r0.what = r1 
1423	            java.lang.String r1 = "back" 
1424	            r0.obj = r1 
1425	            org.cocos2dx.lua.AppActivity r1 = org.cocos2dx.lua.AppActivity.instance 
1426	            r1.sendMessageWith(r0) 
1427	            org.cocos2dx.lua.AppActivity r0 = org.cocos2dx.lua.AppActivity.instance 
1428	            r0.disShowDragbutton() 
1429	            return 
1430	        */ 
1431	        throw new UnsupportedOperationException("Method not decompiled: org.cocos2dx.lua.AppActivity.backButtonClick():void"); 
1432	    } 
1433	 
1434	    @Override // org.cocos2dx.lib.Cocos2dxActivity 
1435	    public void disShowDragbutton() { 
1436	        super.disShowDragbutton(); 
1437	    } 
1438	 
1439	    public void getDataUserAdid() { 
1440	        Adjust.getGoogleAdId(this, new d()); 
1441	    } 
1442	 
1443	    public String getHostIpAddress() { 
1444	        return Utils.getHostIpAddress(this); 
1445	    } 
1446	 
1447	    public void initInstallByChannel() { 
1448	        InstallReferrerClient build = InstallReferrerClient.newBuilder(this).build(); 
1449	        this.referrerClient = build; 
1450	        build.startConnection(new h()); 
1451	    } 
1452	 
1453	    /* JADX INFO: Access modifiers changed from: protected */ 
1454	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity 
1455	    public void onActivityResult(int i2, int i3, Intent intent) { 
1456	        if (-1 == i3) { 
1457	            switch (i2) { 
1458	                case 1000: 
1459	                    photoClipZIP(intent.getData()); 
1460	                    break; 
1461	                case 1001: 
1462	                    photoClipEnd(intent.getExtras()); 
1463	                    break; 
1464	                case 1002: 
1465	                    photoPickEndwer(intent.getData()); 
1466	                    break; 
1467	                case 1003: 
1468	                    contactPickEnd(intent.getData()); 
1469	                    break; 
1470	            } 
1471	        } 
1472	        super.onActivityResult(i2, i3, intent); 
1473	        com.facebook.e eVar = this.callbackManager; 
1474	        if (eVar != null) { 
1475	            eVar.a(i2, i3, intent); 
1476	        } 
1477	    } 
1478	 
1479	    /* JADX INFO: Access modifiers changed from: protected */ 
1480	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity 
1481	    public void onCreate(Bundle bundle) { 
1482	        super.onCreate(bundle); 
1483	        STATIC_REF = getApplicationContext(); 
1484	        getWindow().setFlags(1024, 1024); 
1485	        setRequestedOrientation(nativeIsLandScape() ? 6 : 7); 
1486	        hideNavigationBarDDD(); 
1487	        getWindow().getDecorView().setOnSystemUiVisibilityChangeListener(new e()); 
1488	        this.logger = com.facebook.f0.g.i(this); 
1489	        this.callbackManager = e.a.a(); 
1490	        hostIPAdress = getHostIpAddress(); 
1491	        instance = this; 
1492	        initHandlersss(); 
1493	        this.batteryChangedReceiver = new BatteryChangedReceiver(); 
1494	        registBatter(); 
1495	        initLoginListener(); 
1496	        initShareListener(); 
1497	        ScreenShotListenManager.getInstance().init(this); 
1498	        ScreenShotListenManager.getInstance().setListener(new f()); 
1499	        ScreenShotListenManager.getInstance().startListen(); 
1500	        getURLData(); 
1501	        if (this.__CellularListener == null) { 
1502	            this.__CellularListener = new n(this, null); 
1503	            ((TelephonyManager) instance.getSystemService("phone")).listen(this.__CellularListener, 256); 
1504	        } 
1505	        ThirdParty.getInstance().init(this); 
1506	        this.wifiManager = (WifiManager) getApplicationContext().getSystemService("wifi"); 
1507	        new Timer().scheduleAtFixedRate(new g(), 1000L, 5000L); 
1508	        mFirebaseAnalytics = FirebaseAnalytics.getInstance(this); 
1509	        initInstallByChannel(); 
1510	        TelephonyManager telephonyManager = (TelephonyManager) getSystemService("phone"); 
1511	        String networkCountryIso = telephonyManager.getNetworkCountryIso(); 
1512	        String simCountryIso = telephonyManager.getSimCountryIso(); 
1513	        String country = getResources().getConfiguration().locale.getCountry(); 
1514	        String displayCountry = getResources().getConfiguration().locale.getDisplayCountry(); 
1515	        UserNation = networkCountryIso + "," + simCountryIso + "," + country + "," + displayCountry; 
1516	        getDataUserAdid(); 
1517	    } 
1518	 
1519	    /* JADX INFO: Access modifiers changed from: protected */ 
1520	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity 
1521	    public void onDestroy() { 
1522	        ScreenShotListenManager.getInstance().stopListen(); 
1523	        super.onDestroy(); 
1524	    } 
1525	 
1526	    @Override // android.app.Activity 
1527	    protected void onNewIntent(Intent intent) { 
1528	        super.onNewIntent(intent); 
1529	        setIntent(intent); 
1530	    } 
1531	 
1532	    /* JADX INFO: Access modifiers changed from: protected */ 
1533	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity 
1534	    public void onPause() { 
1535	        super.onPause(); 
1536	    } 
1537	 
1538	    @Override // android.app.Activity 
1539	    public void onRequestPermissionsResult(int i2, String[] strArr, int[] iArr) { 
1540	        super.onRequestPermissionsResult(i2, strArr, iArr); 
1541	        PermissionsUtils.getInstance().onRequestPermissionsResult(this, i2, strArr, iArr); 
1542	    } 
1543	 
1544	    /* JADX INFO: Access modifiers changed from: protected */ 
1545	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity 
1546	    public void onResume() { 
1547	        super.onResume(); 
1548	        getURLData(); 
1549	        setIntent(null); 
1550	        getPackageManager().checkPermission("android.permission.READ_PHONE_STATE", "com.rmyMtU0Nz.gp"); 
1551	    } 
1552	 
1553	    @Override // android.app.Activity 
1554	    public void onStart() { 
1555	        super.onStart(); 
1556	    } 
1557	 
1558	    @Override // android.app.Activity 
1559	    public void onStop() { 
1560	        super.onStop(); 
1561	    } 
1562	 
1563	    @Override // org.cocos2dx.lib.Cocos2dxActivity, android.app.Activity, android.view.Window.Callback 
1564	    public void onWindowFocusChanged(boolean z) { 
1565	        super.onWindowFocusChanged(z); 
1566	        if (z) { 
1567	            hideNavigationBarDDD(); 
1568	        } 
1569	    } 
1570	 
1571	    public void registBatter() { 
1572	        registerReceiver(this.batteryChangedReceiver, getFilter()); 
1573	    } 
1574	 
1575	    public void sendMessage(int i2) { 
1576	        Message obtain = Message.obtain(); 
1577	        obtain.what = i2; 
1578	        this.m_hHandler.sendMessage(obtain); 
1579	    } 
1580	 
1581	    public void sendMessageWith(Message message) { 
1582	        this.m_hHandler.sendMessage(message); 
1583	    } 
1584	 
1585	    public void sendMessageWithObj(int i2, Object obj) { 
1586	        Message obtain = Message.obtain(); 
1587	        obtain.what = i2; 
1588	        obtain.obj = obj; 
1589	        this.m_hHandler.sendMessage(obtain); 
1590	    } 
1591	 
1592	    @Override // org.cocos2dx.lib.Cocos2dxActivity 
1593	    public void setDrabuttonAndShow(Bitmap bitmap, int i2, int i3) { 
1594	        Log.i(ConstDefine.TAG, "DragButton setDrabuttonAndShow"); 
1595	        super.setDrabuttonAndShow(bitmap, i2, i3); 
1596	    } 
1597	 
1598	    public void toLuaFunC(int i2, String str) { 
1599	        AppActivity appActivity; 
1600	        if (-1 == i2 || (appActivity = instance) == null) { 
1601	            return; 
1602	        } 
1603	        appActivity.runOnGLThread(new m(i2, str)); 
1604	    } 
1605	 
1606	    public void toLuaGlobalFunC(String str, String str2) { 
1607	        instance.runOnGLThread(new a(str, str2)); 
1608	    } 
1609	 
1610	    public void unRegistBatter() { 
1611	        unregisterReceiver(this.batteryChangedReceiver); 
1612	    } 
1613	} 
1614	 

Krupa1998370/Krupa1998370 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
