# go-lib-ssv [![](https://godoc.org/github.com/hiyali/go-lib-ssv?status.svg)](http://godoc.org/github.com/hiyali/go-lib-ssv) [![](https://goreportcard.com/badge/github.com/hiyali/go-lib-ssv)](https://goreportcard.com/report/github.com/hiyali/go-lib-ssv) [![](https://travis-ci.org/hiyali/go-lib-ssv.svg?branch=master)](https://travis-ci.org/hiyali/go-lib-ssv) [![](https://img.shields.io/github/license/hiyali/go-lib-ssv)](https://opensource.org/licenses/MIT)

The aim of this repository is simplify the chaos of the SSV

## Verifiers added for

* AdMob [godoc](http://godoc.org/github.com/hiyali/go-lib-ssv/admob) ( [official doc](https://developers.google.com/admob/android/rewarded-video-ssv) | [home page](https://admob.google.com/home/) )
* MoPub [godoc](http://godoc.org/github.com/hiyali/go-lib-ssv/mopub) ( [official doc](https://developers.mopub.com/publishers/android/rewarded-video/#4-configure-the-callback-server) | [home page](https://app.mopub.com/) )

## Quick look

```golang
import "github.com/hiyali/go-lib-ssv/admob"

func adMobVideoRewardedAdHandler(w http.ResponseWriter, r *http.Request) {
  // Magic
  if err := admob.Verify(r.URL); err != nil {
    log.Errorf("Verification failed - err: %v", err)
    return
  }

  // Verified
}
```

admob server callback url look like:
```
https://www.yourdomain.com/path?ad_network=5450213213286189855&ad_unit=12345678&reward_amount=10&reward_item=coins×tamp=1507770365237823&transaction_id=1234567890ABCDEF1234567890ABCDEF&user_id=1234567&signature=MEUCIQDGx44BZgQU6TU4iYEo1nyzh3NgDEvqNAUXlax-XPBQ5AIgCXSdjgKZvs_6QNYad29NJRqwGIhGb7GfuI914MDDZ1c&key_id=1268222887
```

## Lib / Method

| lib.Method | Description |
| --- | --- |
| `admob.Verify(url *url.Url) error` | |
| `mopub.Verify(url *url.Url, secret, verifierKey string) error` | verifierKey usually is `hash`, you'll find secret key in `Rewarded video` tab in `https://app.mopub.com/account` page |

> All libs have `LogEnabled` property

```go
// enable log query raw, default is: false
admob.LogEnabled = true
```

## Test
```
go test ./...
```

## Contribution
> Feel free

## LICENSE

[MIT](https://raw.githubusercontent.com/hiyali/go-lib-ssv/master/LICENSE)
