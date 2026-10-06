# 提示詞與驗收參考

## 從零生成提示詞骨架

只填與該張圖片有關的欄位。修改時重新組合完整提示詞，不引用前一張生成圖。

```text
Use case: photorealistic-natural
Asset type: brand-new 16:9 horizontal editorial press feature image
Primary request: Generate a completely new candid Taiwanese workplace scene for <文章段落目的>. Do not reuse, imitate, edit, composite or face-swap any previous generated image.
Scene/backdrop: <合理場域、空間區隔與時間>
Subject: <人物數量、性別、年齡、職務、誰主導、每人的動作>
People appearance: ordinary Taiwanese workers; natural pores, fine lines, mild fatigue, practical hair and modest workwear; no model styling or beauty retouching.
Composition/framing: <人物互動為主的紀實視角；文字載體退到背景>
Work-object orientation: all documents, photographs, screens and notebooks face their users or the shared work center, never the camera.
Text constraint: no readable text, logos, names, personal data or fake characters; background boards/screens may contain only indistinct shapes and color blocks.
Lighting/mood: natural workplace light, grounded and credible.
Texture quality: coherent skin, hair, fabric, paper, wall, glass and wood texture with subtle non-repeating camera grain.
Avoid: previous-image composition, staged stock-photo symmetry, glamorous faces, waxy skin, crosshatch, grid, repeated texture, malformed hands, duplicated people, holograms and sci-fi AI imagery.
```

## 整組人物矩陣範例

這只是避免重複的規劃方法，不是固定配額：

| 圖片 | 主導角色 | 其他角色 | 主要差異 |
|---|---|---|---|
| 生鮮訂單 | 40 多歲女性行政 | 30 多歲同事、倉儲人員 | 夜間、玻璃辦公室與分貨區 |
| 旅行社 | 50 多歲女性主管 | 30–40 歲女性、20 多歲同事 | 景點資料與退費作業 |
| 財務流程 | 50 多歲資深財務女性 | 30 多歲分析人員 | 文件、帳務系統與知識傳承 |
| 顧問工作坊 | 依文章需求指定 | 跨世代或年輕團隊 | 人物討論為主、白板模糊 |

不要機械套用此表；使用者若指定全員年輕、跨世代、全女性或其他組合，以最新明確指示為準。

## 放大檢查清單

- 臉：左右眼、耳朵、眼鏡腳、髮際線、牙齒、皮膚紋理。
- 手：手指數量、指甲、關節、握筆、托腮、指向、手腕與袖口。
- 文件：裝訂端、頁面上下緣、照片天空方向、閱讀者視線與紙張方向一致。
- 螢幕：內容在玻璃後方，透視貼合邊框，有自然反光與景深；無漂浮感。
- 空間：辦公桌不直接落在倉儲或市場動線；隔間、門把、玻璃反射與前後景連續。
- 材質：皮膚、衣料、牆面、桌面與暗部無週期性波紋或重複貼圖。
- 新聞倫理：不冒充真實企業現場、不沿用企業來源標示、不生成可辨識個資。

任一核心條件不通過時，保留失敗版供比較，重新從零生成下一版；不要以失敗版作為輸入繼續修。
