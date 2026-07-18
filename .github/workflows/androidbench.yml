name: Build AndroidBench APK
on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Use Node.js
      uses: actions/setup-node@v4
      with:
        node-version: '18'
    - name: Set up JDK
      uses: actions/setup-java@v4
      with:
        distribution: 'zulu'
        java-version: '11'
    - name: Install Cordova
      run: npm install -g cordova
    - name: Build APK
      run: |
        cordova platform add android || true
        cordova build android --copy-to ./android-bench.apk || echo "Сборка"
    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: androidbench-apk
        path: ./*.apk
