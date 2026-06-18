const CACHE_NAME = 'musculoskeletal-app-v1';
const ASSETS_TO_CACHE = [
  './index.html',
  './manifest.json',
  'https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css',
  'https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js'
];

// 앱 설치 시 필요한 리소스(HTML, Bootstrap 등)를 태블릿에 다운로드(캐싱)
self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => {
      return cache.addAll(ASSETS_TO_CACHE);
    })
  );
});

// 오프라인 상태일 때 캐싱된 파일로 앱을 구동
self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
