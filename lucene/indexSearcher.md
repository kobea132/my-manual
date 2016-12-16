# org.apache.lucene.[**_IndexSearcher_**](http://lucene.apache.org/core/6_3_0/core/index.html)

> IndexSearcher 是 Lucene 的重點查詢 API，將花點時間解析並了解如何便宜

在這支API的開始，先看官方文檔中是怎麼介紹的:\

---

Implements search over a single IndexReader.

_在**一個** IndexReader上實現查詢_

_是否能夠在多個IndexReader上實現查詢 :question:_

Applications usually need only call the inherited search(Query,int) method. For performance reasons, if your index is unchanging, you should share a single IndexSearcher instance across multiple searches instead of creating a new one per-search. If your index has changed and you wish to see the changes reflected in searching, you should use DirectoryReader.openIfChanged(DirectoryReader) to obtain a new reader and then create a new IndexSearcher from that. Also, for low-latency turnaround it's best to use a near-real-time reader (DirectoryReader.open(IndexWriter)). Once you have a new IndexReader, it's relatively cheap to create a new IndexSearcher from it.

NOTE: IndexSearcher instances are completely thread safe, meaning multiple threads can call any of its methods, concurrently. If your application requires external synchronization, you should not synchronize on the IndexSearcher instance; use your own (non-Lucene) objects instead.

---

