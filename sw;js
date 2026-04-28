const CACHE_NAME = 'haruy-cache-v8';

const ASSETS = [
    ';/',
    './index.html',
    'aula07_html',
    './manifest.json',
    './images/logo.png',
    './images/logopwa.png',
    './images/logopwa512.png',
    './images/banner.png',
    './images/whatsapp.png',
];

self.addEventListener('install', (event) => {
    event.waitUntil(
        caches.open(CACHE_NAME).then((cache) => {
            console.log('Fatiando o sushi no cache!');
            return cache.addAll(ASSETS);
        })
    )
});

self.addEventListener(('fetch'), (event) => {
    event.respondWith(
        caches.match(event.request).then((response) => {
            return response || fetch(event.request);
        })
    )
});

self.addEventListener('activate', (event) => {
    event.waitUntil(
        caches.keys().then((keys) => {
            return Promisse.all(
                keys.filter(key => key !== CACHE_NAME).map(key => caches.delete(key))
            );
        })
    );
});