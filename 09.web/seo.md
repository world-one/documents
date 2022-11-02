### 검색 엔진 최적화(Search engine optimization)
 
- [구글 기본 가이드](https://developers.google.com/search/docs/fundamentals/seo-starter-guide?hl=ko)
- [트위터 카드 마크업 태그](https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup)
- [네이버 가이드](https://searchadvisor.naver.com/guide)
- [OG 공식문서](https://ogp.me/)

```
<title>{title}</title>
<meta name="description" content={description} />
<meta name="keywords" content={keyword} />
<meta name="author" content={author} />
<meta name="robots"
  content={`
    ${robots.noIndex ? 'noindex' : 'index'},
    ${robots.noFollow ? 'nofollow' : 'follow'}
  `}
/>

<meta property="og:site_name" content={og.siteName}/>
<meta property="og:title" content={og.title} />
<meta property="og:description" content={og.description} />
<meta property="og:url" content={og.url} />
<meta property="og:type" content="website" />
<meta property="og:image" content={og.image} />

<meta name="twitter:title" content={title} />
<meta name="twitter:description" content={description} />
<meta name="twitter:creator" content={author} />
<meta name="twitter:site" content="@world-one" />
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:image" content={og.image} />
```