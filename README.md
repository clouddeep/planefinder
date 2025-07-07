# README

## Upgrade

1. Spring Boot: 2.5.4 => 3.5.3
2. Java: 11 => 17
3. Transition from experimental Spring Native project to more stable Spring Boot 3.x with built-in GraalVM Native Image
   support
 
### GraalVM Native Image support

1. **移除 Spring Native 依賴**：
    - Spring Native 是早期的實驗性專案，現已被 Spring Boot 3.x 內建的 Native Image 支援取代
    - 從實驗性質的 `org.springframework.experimental` 套件移除，使用更穩定的方案

2. **更新 native-buildtools 版本**：
    - 使用更穩定的 native-buildtools 版本 (0.9.28)，提高編譯穩定性
    - 註解中明確說明「更新到穩定版本」

3. **配置 Spring Boot Maven Plugin 的 Native Image 支援**：
    - 設定 `<executable>true</executable>` 使構建的 jar 可直接執行
    - 使用 Paketo Buildpacks 的 tiny builder (`paketobuildpacks/builder:tiny`) 減小最終映像大小
    - 啟用 Native Image 編譯 (`BP_NATIVE_IMAGE>true</BP_NATIVE_IMAGE>`)
    - 特別啟用 HTTP 協議支援 (`--enable-url-protocols=http`)，確保應用程式可以進行 HTTP 通訊

4. **添加必要的倉庫**：
    - 添加 Spring Releases 和 Maven Central 倉庫，確保可以獲取所有需要的依賴
    - 這些倉庫配置同時添加到 repositories 和 pluginRepositories 區段，確保依賴和插件都能正確下載
