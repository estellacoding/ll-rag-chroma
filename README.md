# RAG 實作: LangChain vs. LlamaIndex
本專案用 LangChain 和 LlamaIndex，實現檢索生成系統(Retrieval Augmented Generation, RAG)，結合 OpenAI 嵌入模型與 Chroma 向量資料庫，將文件內容向量化，可高效檢索並準確回答與 MetaGPT 論文相關的問題。

# 主要功能
- 實作 LangChain RAG
- 實作 LlamaIndex RAG
- 檢索 [MetaGPT](https://arxiv.org/abs/2308.00352) 文件

# 處理流程
- 文本讀取
- 文本分割: 分割文本為較小片段(chunk)
- 向量化: 使用嵌入模型將文本轉換為向量
- 向量資料庫: 建立向量索引
- 儲存: 儲存索引和向量，便於後續使用
- 生成回應: GPT根據查詢＋檢索上下文生成最終回答

# LangChain vs. LlamaIndex
|步驟|LangChain|LlamaIndex|
|-|-|-|
|讀取|`DocumentLoader`的`PyPDFLoader`從來源讀取文本|`SimpleDirectoryReader`從資料夾中讀取文件|
|分割|使用`TextSplitter`的`RecursiveCharacterTextSplitter`分割文本為較小片段(chunk)|自動默認 `RecursiveTextSplitter`|
|向量化|`OpenAIEmbeddings`將文本轉換為向量|`OpenAIEmbeddings`|
|資料庫|`VectorstoreIndexCreator`自動完成文本分割、向量化、索引建立和向量資料庫的設定|使用`VectorStoreIndex`更靈活配置|
|儲存|`persist_directory`儲存和指定`Chroma`為向量資料庫|使用`ChromaVectorStore`|
