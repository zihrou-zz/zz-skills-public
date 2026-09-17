# RD Ready 契約

只在產出契約或判斷 readiness 時讀取本檔。

## 預設結構

### 1. Intent

- 問題、目標使用者與觸發時刻。
- 現況及可驗證證據。
- 期望結果、成功指標與取得方式。
- 本次 appetite／時程約束。
- In scope、later、out of scope。

### 2. Behavior Spine

每條端到端行為切片使用 `B-###`：

- Actor、Trigger、Context、Goal。
- Entry、逐步行為、每步系統回饋。
- 使用者決定點與系統判斷點。
- Success／abandon／failure exits。
- interruption、resume、retry、handoff。
- 頻率、資料量、時限、裝置或操作環境。

先寫一條可交付的主路徑，再擴充變體。不要按 frontend／backend 分割行為。

### 3. Domain and State

- 穩定名詞、角色與權限意圖。
- 核心實體及關係，只描述產品需要的概念。
- 可觀察狀態、合法轉換、觸發者、可逆性與終止狀態。

### 4. Rules and Decisions

- 業務規則使用 `R-###`，寫明條件、結果、優先序與適用範圍。
- 決策使用 `D-###`，記錄選擇、替代方案、理由、決策人、日期與會受影響的 ID。
- 衝突規則必須有顯式優先序；不可依文件順序暗示。

### 5. Data, Dependencies and Failure Policy

- 資料來源、權威來源、新鮮度、缺值含義與識別鍵。
- 外部系統、人工步驟、前置工作與 owner。
- 每個依賴失敗時為 fail-open、fail-closed、degrade 或人工處理。
- 重試、冪等、併發、歷史資料、遷移、稽核與 observability 僅在相關時展開。

### 6. Executable Examples

以 `E-###` 記錄具體 Given／When／Then，並引用 `B-###`、`R-###`。重要規則至少有正常例與邊界例；高風險規則另含失敗與恢復案例。

### 7. Constraints and Technical Checkpoint

- 法規、安全、隱私、效能、可用性、相容性、成本與既有架構限制。
- 分開標示產品約束與 RD 技術選擇。
- RD 的技術方案若改變行為、成本、時程、資料風險或可逆性，建立新的共同決策。

### 8. Delivery Slices

- 以可演示、可驗收的端到端行為切片拆分。
- 每個 task 引用相應 `B/R/E/D` ID。
- 明示依賴、完成證據與不包含內容。

### 9. Open Items and Readiness

每個 open item 必須是：

- `BLOCKING_PRODUCT`：需求方必須決定，未解不得開發相關切片。
- `BLOCKING_EVIDENCE`：需取得外部證據，標 owner／來源／期限。🔴 **只用在「連 RD 也查不到、要等外部回覆」的事。** 需求方沒權限、但 RD 自己查得到的既有系統事實，歸 `TECHNICAL_DESIGN`，不歸這裡——把它當阻塞項，需求書就永遠送不出去。
- `TECHNICAL_DESIGN`：由 RD 在不改變產品契約下決定。
- `LATER`：明確不在本次範圍。

## Readiness 等級

- `DISCOVERY`：問題或主要行為仍不清楚。
- `PRODUCT_READY`：產品行為與邊界已定，等待 RD 技術設計 checkpoint。
- `RD_READY`：可估工、拆卡、實作與驗收；沒有 `BLOCKING_PRODUCT` 或 `BLOCKING_EVIDENCE`。

## RD Ready Gate

只有下列相關項目全部有證據才可標 `RD_READY`：

- 主要使用者可從觸發到完成完整回放工作流程。
- 每個系統動作都能追到使用者目的，每個關鍵步驟都有回饋與下一步。
- 中斷、返回、重試、重複操作與角色交接已有處置。
- 每個 in-scope 行為都有可觀察結果與驗收案例。
- 重要規則有正常與邊界案例，衝突時有明確優先序。
- 狀態有進入、離開、權限、可逆性與終止條件。
- 外部資料失敗與缺值政策明確，不以空值偷偷放行。
- 「要請 RD 確認的事實」那一節每條都寫了影響哪幾段與目前暫時假設。
- 人工覆寫有資格、原因、影響與留痕。
- 成功指標可取得；高風險非功能限制已量化或明確排除。
- 歷史資料與上線／回滾策略在相關時已決定。
- 所有需求可追到行為、決策、驗收與任務。
- 沒有需要需求方回答的阻塞問題。

最後做 teach-back：請 RD 或以 RD 視角只依契約重述主流程、列出實作切片與剩餘問題。將問題分類；只要仍有產品決策問題，就退回 `PRODUCT_READY` 或 `DISCOVERY`，不可宣稱完成。
