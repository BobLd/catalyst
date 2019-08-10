<img src="https://raw.githubusercontent.com/curiosity-ai/catalyst/master/Catalyst/catalyst.png?token=ACDCOAYAIML2KGJTHTJP27C5KGCEC"/>

<a href="https://curiosity.ai"><img src="https://curiosity.ai/assets/images/logos/curiosity.png" width="100" height="100" align="right" /></a>

_**catalyst**_ is a C# Natural Language Processing library built for speed. Inspired by spaCy's design, it brings pre-trained models, out-of-the box support for training word and document embeddings, and flexible entity recognition models.


## ✨ Getting Started

Using _**catalyst**_ is as simple as installing its [NuGet Package](https://www.nuget.org/packages/Catalyst), and setting the storage to use our online repository. This way, models will be lazy loaded either from disk or downloaded from our online repository.

```csharp
Storage.Current = new OnlineRepositoryStorage(new DiskStorage("catalyst-models"));
var nlp = await Pipeline.ForAsync(Language.English);
var doc = new Document("The quick brown fox jumps over the lazy dog", Language.English);
nlp.ProcessSingle(doc);
Console.WriteLine(doc.ToJson());
```

You can also take advantage of C# lazy evaluation and native multi-threading support to process a large number of documents in parallel:

```csharp
var docs = GetDocuments();
var parsed = nlp.Process(docs);
DoSomething(parsed);

IEnumerable<IDocument> GetDocuments()
{
    //Generates a few documents, to demonstrate multi-threading & lazy evaluation
    for(int i = 0; i < 1000; i++)
	{
        yield return new Document("The quick brown fox jumps over the lazy dog", Language.English);
	}
}

void DoSomething(IEnumerable<IDocument> docs)
{
    foreach(var doc in docs)
    {
        Console.WriteLine(doc.ToJson());
    }
}
```


## 📖 Documentation

| Documentation     |                                                                |
| ----------------- | -------------------------------------------------------------- |
| [Getting Started] | How to use _**catalyst**_ and its features.                          |
| [API Reference]   | The detailed reference for _**catalyst**_'s API.                     |
| [Contribute]      | How to contribute to _**catalyst**_ codebase.                  |

[Getting Started]: https://catalyst.curiosity.ai/getting-started
[api reference]: https://catalyst.curiosity.ai/api
[contribute]: https://github.com/curiosity-ai/catalyst/blob/master/CONTRIBUTING.md
