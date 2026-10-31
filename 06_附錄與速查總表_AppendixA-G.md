# 給 C# 工程師的 Angular 系統化學習教材（六）：附錄與速查總表（附錄 A～G）

> 🏠 [回總目錄 (README)](./README.md) ｜ ⬅️ [上一篇：05_容器部署升級與未來趨勢_Ch18-20](./05_容器部署升級與未來趨勢_Ch18-20.md) ｜ ➡️ 末篇

## 本篇目錄

- [附錄 A 常用術語](#附錄-a-常用術語)
- [附錄 B 官方參考資料](#附錄-b-官方參考資料)
- [附錄 C C# / .NET ↔ Angular / TypeScript 對照總表](#附錄-c-c--net--angular--typescript-對照總表)
- [附錄 D 舊語法 → Angular 22 語法對照表](#附錄-d-舊語法--angular-22-語法對照表)
- [附錄 E 七篇來源文章的校正總表](#附錄-e-七篇來源文章的校正總表)
- [附錄 F Angular 22 升級後要搜尋的關鍵字](#附錄-f-angular-22-升級後要搜尋的關鍵字)
- [附錄 G 指令速查](#附錄-g-指令速查)

---

## 附錄 A 常用術語

| 原文 | 本教材用語 | 意義與補充說明 |
|---|---|---|
| Component | 元件 | 有範本、狀態與行為的畫面單位 |
| Template | 範本 | 描述狀態如何呈現為畫面 |
| Binding | 繫結 | 將資料或事件接到元素／元件 |
| Directive | 指令 | 不帶範本、附加於元素或範本以改變行為的類別（例如 `routerLink`） |
| Pipe | Pipe／顯示轉換 | 範本裡的格式化函式（如 `{{ price \| currency }}`，類似 C# `ToString("C")`） |
| Service | 服務 | 封裝可注入的共用行為或狀態 |
| Dependency injection | 相依性注入 | 由框架解析與提供相依實例 |
| Standalone component | 獨立元件 | 自行列出範本相依，不需在 NgModule 宣告 |
| NgModule | 舊式模組 | 舊的模組化機制，現代 Angular 已由獨立元件取代，入門可略過 |
| Signal | Signal | 具有相依追蹤與更新通知的值容器 |
| Observable | Observable | 隨時間發出值及完成／錯誤通知的抽象 |
| Change detection | 變更偵測 | 檢查並更新畫面繫結的機制 |
| Bundle / chunk | 打包檔／程式碼區塊 | `ng build` 產出的 JS 載入單位；主要套件（main bundle）越小，首頁載入越快 |
| Lazy loading | 延遲載入 | 到需要時才下載或初始化 |
| `@defer` | 延後載入區塊 | 範本區塊延後載入語法（例如進入可視範圍才載入，見第 15.2 節） |
| CSR / SSR / SSG | 渲染模式 | 瀏覽器端渲染 / 伺服器端渲染 / 靜態網站產生（見第 15.4 節） |
| Hydration | 水合 | 瀏覽器接手 SSR 產生的靜態 HTML 並綁上事件，不必重畫；增量式水合為逐區塊接管 |
| Schematics | 程式碼遷移與產生器 | Angular CLI 的程式碼產生／改寫腳本，`ng generate` 與 `ng update` 背後的機制 |
| Entry point | 進入點 | 套件公開的匯入路徑與 API 邊界 |
| Builder | 建置器 | 執行 Angular 工作區某個目標的工具 |
| Runtime configuration | 執行階段設定 | 部署或啟動時才決定的公開設定 |
| Reverse proxy | 反向代理 | 接受外部請求，再轉送到後端服務 |

---

## 附錄 B 官方參考資料

來源文章對應見第 0.2 節。以下官方資料用於確認 API、版本及工具行為；連結內容可能隨後續版本更新，重現範例以鎖定檔及當時版本文件為準。

| 編號 | 官方資料 | 對應主題 |
|---|---|---|
| O1 | [Angular versioning and releases][O1] | 正式版本與後續時程 |
| O2 | [Angular version compatibility][O2] | Node.js、TypeScript、RxJS 範圍 |
| O3 | [TypeScript for Java/C# programmers][O3] | 結構型別與執行模型 |
| O4 | [Making HTTP requests][O4] | HttpClient、回應型別與訂閱 |
| O5 | [Angular components][O5] | 元件與範本 |
| O6 | [Component lifecycle][O6] | 生命週期 |
| O7 | [Angular Signals][O7] | 反應式狀態 |
| O8 | [Advanced component configuration][O8] | OnPush 與 Eager |
| O9 | [Zoneless][O9] | 無 Zone.js 更新機制 |
| O10 | [Service API][O10] | 新版服務宣告 |
| O11 | [Define routes][O11] | 路由與匹配 |
| O12 | [ASP.NET Core Minimal APIs][O12] | C# API 與驗證 |
| O13 | [Reactive data fetching with httpResource][O13] | 查詢與請求狀態 |
| O14 | [Async reactivity with resources][O14] | Resource 值與錯誤 |
| O15 | [Reactive forms][O15] | FormControl 與 FormGroup |
| O16 | [Comparison with other form systems][O16] | 表單方式比較 |
| O17 | [Signal Forms submission][O17] | Signal Forms 提交 |
| O18 | [HTTP testing][O18] | HttpTestingController |
| O19 | [Angular security][O19] | XSS 與框架安全邊界 |
| O20 | [Deferred loading with @defer][O20] | 區塊延後載入 |
| O21 | [Lazy loading services][O21] | injectAsync |
| O22 | [Creating libraries][O22] | 公開 API 與函式庫流程 |
| O23 | [Angular Package Format][O23] | 套件格式與部分編譯 |
| O24 | [Angular Custom Elements][O24] | Angular Elements |
| O25 | [createApplication API][O25] | 獨立建立應用程式環境 |
| O26 | [Docker multi-stage builds][O26] | 多階段映像檔 |
| O27 | [Nginx try_files][O27] | 靜態檔案與 SPA fallback |
| O28 | [Angular migrations][O28] | CLI 遷移工具 |
| O29 | [Angular CLI MCP][O29] | AI 工具整合 |
| O30 | [Angular Update Guide][O30] | 版本升級 |
| O31 | [Template expression syntax][O31] | 可選串連與空值語意 |
| O32 | [RouterConfigOptions][O32] | 路由參數繼承 |
| O33 | [withXhr API][O33] | 上傳進度與後端選擇 |
| O34 | [provideClientHydration API][O34] | 水合預設功能 |
| O35 | [Server and hybrid rendering][O35] | CSR、SSR 與 prerender |
| O36 | [Signal Forms essentials][O36] | 欄位繫結與模型 |

[O1]: https://angular.dev/reference/releases
[O2]: https://angular.dev/reference/versions
[O3]: https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes-oop.html
[O4]: https://angular.dev/guide/http/making-requests
[O5]: https://angular.dev/essentials/components
[O6]: https://angular.dev/guide/components/lifecycle
[O7]: https://angular.dev/guide/signals
[O8]: https://angular.dev/guide/components/advanced-configuration
[O9]: https://angular.dev/guide/zoneless
[O10]: https://angular.dev/api/core/Service
[O11]: https://angular.dev/guide/routing/define-routes
[O12]: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis?view=aspnetcore-10.0
[O13]: https://angular.dev/guide/http/http-resource
[O14]: https://angular.dev/guide/signals/resource
[O15]: https://angular.dev/guide/forms/reactive-forms
[O16]: https://angular.dev/guide/forms/signals/comparison
[O17]: https://angular.dev/guide/forms/signals/form-submission
[O18]: https://angular.dev/guide/http/testing
[O19]: https://angular.dev/best-practices/security
[O20]: https://angular.dev/guide/templates/defer
[O21]: https://angular.dev/guide/di/lazy-loading-services
[O22]: https://angular.dev/tools/libraries/creating-libraries
[O23]: https://angular.dev/tools/libraries/angular-package-format
[O24]: https://angular.dev/guide/elements
[O25]: https://angular.dev/api/platform-browser/createApplication
[O26]: https://docs.docker.com/build/building/multi-stage/
[O27]: https://nginx.org/en/docs/http/ngx_http_core_module.html#try_files
[O28]: https://angular.dev/reference/migrations
[O29]: https://angular.dev/ai/mcp
[O30]: https://angular.dev/update-guide
[O31]: https://angular.dev/guide/templates/expression-syntax
[O32]: https://angular.dev/api/router/RouterConfigOptions
[O33]: https://angular.dev/api/common/http/withXhr
[O34]: https://angular.dev/api/platform-browser/provideClientHydration
[O35]: https://angular.dev/guide/ssr
[O36]: https://angular.dev/essentials/signal-forms

---

## 附錄 C C# / .NET ↔ Angular / TypeScript 對照總表

| C# / .NET | Angular / TypeScript | 參考章節 |
|---|---|---|
| Attribute `[X]` | Decorator `@X()` | 1.5、2.8 |
| `using` / namespace | `import` / `export` | 1.5、2.7 |
| `var` 型別推斷 | `let` / `const` 型別推斷 | 2.2 |
| `null` | `null` **和** `undefined` | 2.3 |
| lambda `x => x.Y` | 箭頭函式 `x => x.y` | 2.4 |
| LINQ `Where` / `Select` / `FirstOrDefault` | `filter` / `map` / `find` | 2.1、2.4 |
| `Task<T>` / `async` `await` | `Promise<T>` / `async` `await` | 3.1、3.2 |
| `IObservable<T>`（Rx.NET） | RxJS `Observable<T>` | 3.2、3.6 |
| `record` / DTO | `interface` | 2.1、2.3、9.3 |
| `$"..."` 字串插補 | 反引號 `` `...${x}` `` | 3.1、6.6 |
| Razor Component / WPF UserControl | `@Component` 元件 | 5.1、5.6 |
| `@if` / `@foreach`（Razor） | `@if` / `@for`（範本控制流程） | 5.3、5.6 |
| XAML Binding `{Binding X}` | `[prop]="x()"` / `{{ x() }}` | 5.2、5.6 |
| `@onclick` / `Click +=` | `(click)="handler()"` | 5.2、5.6 |
| `INotifyPropertyChanged` | `signal()` | 6.1、6.6 |
| 計算屬性（手動通知） | `computed()` | 6.1、6.6 |
| `PropertyChanged` handler | `effect()` | 6.3、6.6 |
| `DependencyProperty` / `[Parameter]` | `input()` | 7.2、7.6 |
| `event` / `EventHandler` | `output()` | 7.2、7.6 |
| `AddSingleton<T>()` | `@Service()` / `@Injectable({ providedIn: 'root' })` | 7.3、7.7 |
| 建構函式注入 | `inject()` | 7.3、7.7 |
| `Program.cs` DI 註冊 | `app.config.ts` `providers` | 1.6、9.4 |
| `MapControllerRoute` / `[Route]` | `Routes` 陣列 | 8.2、8.6 |
| `@RenderBody()` | `<router-outlet />` | 8.3、8.6 |
| `HttpClient` + `DelegatingHandler` | `HttpClient` + interceptor | 3.1、19.8.2 |
| `IsBusy` / `Error` / `Data` + `CancellationToken` | `httpResource()` | 10.1、10.5 |
| `Lazy<Task<T>>` / 動態載入組件 | `injectAsync()` | 15.3、15.5 |
| `<Nullable>enable</Nullable>` | `strictTemplates` | 19.3、19.8.2 |
| Roslyn Analyzer + Code Fix | `ng generate @angular/core:*` schematics | 1.5、19.1、19.9 |
| `dotnet nuget locals all --clear` | `ng cache clean` | 19.1、19.9.3 |
| COM / ActiveX 元件 | Web Components（`@angular/elements`） | 17.1、17.5 |
| `.nupkg` 多組件類別庫 | 多進入點函式庫 | 16.3、16.5 |
| 組件 metadata / reference assembly | `.d.ts` 型別宣告檔 | 16.1、16.5.6 |
| `sdk` → `aspnet` 多階段 Dockerfile | `node` → `nginx` 多階段 Dockerfile | 18.2、18.9.4 |
| `MapFallbackToFile("index.html")` | Nginx `try_files ... /index.html` | 8.6、18.3、18.9.5 |
| `appsettings.json`（伺服器端，私密） | `environment.ts` / `app-config.json`（打包或傳送至瀏覽器，**公開**） | 1.5、9.4、18.7、18.9.8 |

---

## 附錄 D 舊語法 → Angular 22 語法對照表

讀網路上的 Angular 文章（包括本教材的七篇原文）時，常會遇到舊寫法。下表幫你即時翻譯；右欄是本教材各章節採用的寫法。

| 主題 | 舊語法 | Angular 22 語法 | 自動遷移指令 |
|---|---|---|---|
| 元件宣告 | `standalone: true` | 省略（預設即獨立元件） | `ng update` |
| 類別／檔名 | `UserCardComponent` / `user-card.component.ts` | `UserCard` / `user-card.ts` | 新專案預設 |
| 變更偵測 | 不寫（Default）或 `ChangeDetectionStrategy.OnPush` | 不寫（預設 OnPush）；舊元件由遷移加上 `Eager` | `ng update` |
| 條件渲染 | `<div *ngIf="x; else tpl">` | `@if (x) { } @else { }` | `@angular/core:control-flow` |
| 迴圈 | `<li *ngFor="let u of users; trackBy: fn">` | `@for (u of users(); track u.id) { }` | `@angular/core:control-flow` |
| 多分支 | `[ngSwitch]` / `*ngSwitchCase` | `@switch (x) { @case (1) { } @default { } }` | `@angular/core:control-flow` |
| 輸入 | `@Input() name = '';` | `name = input('');` | `@angular/core:signal-input-migration` |
| 必填輸入 | `@Input({ required: true }) id!: string;` | `id = input.required<string>();` | 同上 |
| 輸出 | `@Output() saved = new EventEmitter<void>();` | `saved = output<void>();` | `@angular/core:output-migration` |
| 雙向繫結 | `@Input() value; @Output() valueChange` | `value = model<string>();` | ─ |
| 查詢子元素 | `@ViewChild(Child) child!: Child;` | `child = viewChild.required(Child);` | `@angular/core:signal-queries-migration` |
| 元件狀態 | `count = 0; this.count++;` | `count = signal(0); this.count.update(c => c + 1);` | ─（手動） |
| 衍生值 | getter 或 `ngOnChanges` 重算 | `computed(() => ...)` | ─ |
| 服務宣告 | `@Injectable({ providedIn: 'root' })` | `@Service()` | ─ |
| 注入 | `constructor(private http: HttpClient) {}` | `private http = inject(HttpClient);` | `@angular/core:inject` |
| 延遲載入服務 | 無 | `injectAsync(() => import('./pdf.service'))` | ─ |
| 啟動初始化 | `{ provide: APP_INITIALIZER, useFactory, deps, multi: true }` | `provideAppInitializer(() => { ... })` | ─ |
| HTTP 讀取 | `http.get().subscribe({ next, error })` + 三個狀態欄位 | `httpResource<T>(() => url)` | ─ |
| HttpClient 設定 | `provideHttpClient(withFetch())` | `provideHttpClient()` | `ng update` |
| 上傳進度 | `{ reportProgress: true, observe: 'events' }` | `{ reportUploadProgress: true, observe: 'events' }` | ─ |
| 表單 | `new FormGroup({ email: new FormControl('', [Validators.required]) })` | `form(signal({ email: '' }), f => { required(f.email); })` | ─ |
| 表單繫結 | `[formControl]` / `formControlName` | `[formField]="login.email"` | ─ |
| 路由元件 | `{ path: 'x', component: X }` | `{ path: 'x', loadComponent: () => import('./x').then(m => m.X) }` | `@angular/core:route-lazy-loading` |
| 延後載入區塊 | 無 | `@defer (on viewport) { } @placeholder { }` | ─ |
| 範本 `?.` | 回傳 `null` | 回傳 `undefined`（與 TypeScript 一致） | `ng update`（以 `$safeNavigationMigration` 標記） |
| 水合 | `provideClientHydration(withIncrementalHydration())` | `provideClientHydration()`（預設增量式） | `ng update` |
| 模組 | `@NgModule({ declarations, imports, exports })` | 不需要；直接在元件 `imports: []` | `@angular/core:standalone` |

---

## 附錄 E 七篇來源文章的校正總表

彙整自本教材第 0.3 節，並對應到本教材加註校正的位置：

| 容易造成誤解的說法 | 本教材採用的解釋 | 位置 |
|---|---|---|
| FormGroup 已棄用 | Reactive Forms 仍受支援；Signal Forms 是另一種正式穩定的做法 | 0.3、12.4、19.8.2 |
| Node 22 以上都能使用 | 必須符合官方相容表的範圍（`^22.22.3 \|\| ^24.15.0 \|\| ^26.0.0`），不能只比主要版本 | 0.3、4.5.1 |
| Signals 取代所有 RxJS | Signals 表達目前狀態；RxJS 處理多次事件、時間與非同步流程；兩者搭配 | 0.3、3.6、20.5.1 |
| OnPush 只看 input | 範本讀取的 Signal、事件、AsyncPipe、`markForCheck()` 都會影響檢查排程；OnPush 與 zoneless 是兩件事 | 0.3、6.4、6.7 |
| 升級一定自動變快 | 升級不會消除 API 太慢、大量 DOM、無效查詢與不必要的運算 | 0.3、19.8.5、20.5.2 |
| Web Component 不需要 Angular | 對外是瀏覽器標準介面，但 Angular Elements 仍需 Angular 執行環境 | 0.3、17.1、17.5.4、17.5.9 |
| Docker 環境變數會自動改 Angular | 已編譯的 JS 不讀容器 ENV，必須建立明確的設定載入流程 | 0.3、18.7、18.9.8 |
| httpResource 自動處理就不需測試 | 仍需測試參數、回應格式、失敗狀態與寫入後重新載入 | 0.3、10.3、14.2 |
| `injectAsync(() => import('./x'))` 簡寫 | 命名匯出要加 `.then(m => m.X)` | 15.3、15.5、19.8.2 |
| 用 `!value` 修 `?.` 的語意變更 | `!value` 也涵蓋 `false`、`0`、空字串；「不存在」用 `== null` | 19.5、19.8.2 |
| 22.3 函式庫建置器可直接使用 | 查核時（2026-10-31）正式版為 22.2.4，官方仍以 ng-packagr 為準；列為後續研究 | 0.3、16.4、16.5.1 |
| 預設增量式水合 | 前提是已採用 SSR 與 hydration；純 SPA 不會自動多出 SSR | 15.4、19.8.5 |

---

## 附錄 F Angular 22 升級後要搜尋的關鍵字

| 關鍵字 | 代表意義 |
|---|---|
| `Eager` | 遷移程序替舊元件加上的變更偵測策略；改用 signals 後可逐一移除 |
| `withXhr` | 遷移程序判斷需要保留 XHR 的地方（通常是上傳進度） |
| `strictTemplates: false` | 專案原本未啟用嚴格範本檢查；修完後移除 |
| `$safeNavigationMigration` | 範本中依賴 `?.` 回傳 `null` 的運算式；逐一改寫 |
| `paramsInheritanceStrategy` | 若巢狀路由需要獨立參數，明確設為 `'emptyOnly'` |

---

## 附錄 G 指令速查

```bash
# 建立與執行
npm install -g @angular/cli
ng new my-app
npm start                                   # = ng serve

# 產生
ng generate component user-card            # ng g c user-card
ng generate service cart                   # ng g s cart
ng generate component user-card --dry-run  # 預覽

# 建置與分析
ng build --configuration production
ng build --stats-json

# 遷移（每次一項、各自提交）
ng generate @angular/core:control-flow
ng generate @angular/core:cleanup-unused-imports
ng generate @angular/core:signal-input-migration --insert-todos
ng generate @angular/core:output-migration
ng generate @angular/core:signal-queries-migration
ng generate @angular/core:inject
ng generate @angular/core:route-lazy-loading

# 升級
ng update
ng update @angular/core@22 @angular/cli@22

# 維護
ng cache info
ng cache clean

# AI 助理
npx @angular/cli mcp

# Docker
docker build -t angular-docker-demo:1.0 .
docker run -d --name angular-app -p 8080:80 angular-docker-demo:1.0
docker logs angular-app
```

---

> 🏠 [回總目錄 (README)](./README.md) ｜ ⬅️ [上一篇：05_容器部署升級與未來趨勢_Ch18-20](./05_容器部署升級與未來趨勢_Ch18-20.md) ｜ ➡️ 末篇