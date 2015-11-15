##### How do I generate sitemap in Golang?

    ```go
    package main

    import (
        "github.com/ikeikeikeike/go-sitemap-generator/stm"
    )


    func main() {
        sm := stm.NewSitemap()
        sm.SetDefaultHost("http://example.com")
        sm.SetSitemapsPath("sitemap/example.com")

        sm.Create()

        sm.Add(stm.URL{"loc": "home", "changefreq": "always", "mobile": true})
        sm.Add(stm.URL{"loc": "readme"})
        sm.Add(stm.URL{"loc": "aboutme", "priority": 0.1})

        sm.Finalize().PingSearchEngines()
    }
    ```

#### News Sitemaps

    ```go
    sm.Add(stm.URL{"loc": "/news", "news": stm.URL{
        "publication": stm.URL{
            "name":     "Example",
            "language": "en",
        },
        "title":            "My Article",
        "keywords":         "my article, articles about myself",
        "stock_tickers":    "SAO:PETR3",
        "publication_date": "2011-08-22",
        "access":           "Subscription",
        "genres":           "PressRelease",
    }})
    ```

#### How to testing

```
$ (cd ./stm ; go test -v github.com/ikeikeikeike/go-sitemap-generator/stm...)
```
