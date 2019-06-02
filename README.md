# AutoCompleteTextViewIssue

This demonstrates a couple of bugs in AutoCompleteTextView using the following releases:

    implementation 'androidx.appcompat:appcompat:1.1.0-alpha05'
    implementation 'com.google.android.material:material:1.1.0-alpha06'

i) After selecting an item in the AutoCompleteTextView, then rotating the display to re-create the Activity the
AutoCompleteTextView then only shows the selected option as available, the other options from the list vanish.

ii) Rotating the display while the choice list pop-out is visible can cause the following crash

E/AndroidRuntime: FATAL EXCEPTION: main
    Process: com.greatape.autocompletetextviewissue, PID: 17928
    java.lang.RuntimeException: Unable to start activity ComponentInfo{com.greatape.autocompletetextviewissue/com.greatape.autocompletetextviewissue.MainActivity}: android.view.WindowManager$BadTokenException: Unable to add window -- token null is not valid; is your activity running?
        at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2957)
        at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:3032)
        at android.app.ActivityThread.handleRelaunchActivity(ActivityThread.java:4921)
        at android.app.ActivityThread.-wrap19(Unknown Source:0)
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1702)
        at android.os.Handler.dispatchMessage(Handler.java:105)
        at android.os.Looper.loop(Looper.java:164)
        at android.app.ActivityThread.main(ActivityThread.java:6944)
        at java.lang.reflect.Method.invoke(Native Method)
        at com.android.internal.os.Zygote$MethodAndArgsCaller.run(Zygote.java:327)
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:1374)
     Caused by: android.view.WindowManager$BadTokenException: Unable to add window -- token null is not valid; is your activity running?
        at android.view.ViewRootImpl.setView(ViewRootImpl.java:958)
        at android.view.WindowManagerGlobal.addView(WindowManagerGlobal.java:381)
        at android.view.WindowManagerImpl.addView(WindowManagerImpl.java:100)
        at android.widget.PopupWindow.invokePopup(PopupWindow.java:1467)
        at android.widget.PopupWindow.showAsDropDown(PopupWindow.java:1316)
        at android.widget.ListPopupWindow.show(ListPopupWindow.java:740)
        at android.widget.AutoCompleteTextView.showDropDown(AutoCompleteTextView.java:1226)
        at com.google.android.material.textfield.DropdownMenuEndIconDelegate.showHideDropdown(DropdownMenuEndIconDelegate.java:177)
        at com.google.android.material.textfield.DropdownMenuEndIconDelegate.access$600(DropdownMenuEndIconDelegate.java:48)
        at com.google.android.material.textfield.DropdownMenuEndIconDelegate$3.onClick(DropdownMenuEndIconDelegate.java:150)
        at android.view.View.performClick(View.java:6897)
        at com.google.android.material.textfield.TextInputLayout.onRestoreInstanceState(TextInputLayout.java:1973)
        at android.view.View.dispatchRestoreInstanceState(View.java:18887)
        at android.view.ViewGroup.dispatchRestoreInstanceState(ViewGroup.java:3930)
        at com.google.android.material.textfield.TextInputLayout.dispatchRestoreInstanceState(TextInputLayout.java:1983)
        at android.view.ViewGroup.dispatchRestoreInstanceState(ViewGroup.java:3936)
        at android.view.ViewGroup.dispatchRestoreInstanceState(ViewGroup.java:3936)
        at android.view.ViewGroup.dispatchRestoreInstanceState(ViewGroup.java:3936)
        at android.view.ViewGroup.dispatchRestoreInstanceState(ViewGroup.java:3936)
        at android.view.View.restoreHierarchyState(View.java:18865)
        at com.android.internal.policy.PhoneWindow.restoreHierarchyState(PhoneWindow.java:2248)
        at android.app.Activity.onRestoreInstanceState(Activity.java:1153)
        at android.app.Activity.performRestoreInstanceState(Activity.java:1108)
        at android.app.Instrumentation.callActivityOnRestoreInstanceState(Instrumentation.java:1266)
        at android.app.ActivityThread.performLaunchActivity(ActivityThread.java:2930)
        at android.app.ActivityThread.handleLaunchActivity(ActivityThread.java:3032) 
        at android.app.ActivityThread.handleRelaunchActivity(ActivityThread.java:4921) 
        at android.app.ActivityThread.-wrap19(Unknown Source:0) 
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:1702) 
        at android.os.Handler.dispatchMessage(Handler.java:105) 
        at android.os.Looper.loop(Looper.java:164) 
        at android.app.ActivityThread.main(ActivityThread.java:6944) 
        at java.lang.reflect.Method.invoke(Native Method) 
        at com.android.internal.os.Zygote$MethodAndArgsCaller.run(Zygote.java:327) 
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:1374) 
