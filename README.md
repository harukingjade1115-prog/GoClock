# モーニングタイマー PWA 追加ファイル
このフォルダの `manifest.json` と `sw.js` を、あなたの `timer.html / tasks.html / history.html` と同じディレクトリに置いてください。

さらに、各 HTML の `<head>` に以下を追加：

```html
<link rel="manifest" href="manifest.json">
<meta name="theme-color" content="#007aff">
```

そして、各 HTML の一番下（`</body>`直前）に以下を追加：

```html
<script>
if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('/sw.js');
  });
}
</script>
```

これで HTTPS 上に公開すれば、ホーム画面に追加でき、オフラインでも動く PWA になります。
例の無料ホスティング：GitHub Pages / Cloudflare Pages / Netlify など。

## iOS/Android のストアアプリ化（任意）
1) Node.js を入れる
2) `npm create @ionic/cli@latest` で空プロジェクト→`src`にこの3つの HTML を置くか、`public/`に配置
3) Capacitor を導入し `npx cap add ios android`
4) `npx cap copy` → Xcode / Android Studio でビルドして提出
