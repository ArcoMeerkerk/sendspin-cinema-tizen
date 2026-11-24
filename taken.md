# Taken voor Sendspin Cinema op Samsung TV

## 1. GitHub-module toevoegen in TizenBrew

- [x] Controleer of de module beschikbaar is. jsDelivr gaf HTTP 200 voor het manifest van `ArcoMeerkerk/sendspin-cinema-tizen` met en zonder `@latest`. De automatische updater staat in commit `03f1950`.
- [x] Zoek de code achter het veld dat leeg wordt na **Gereed**. [TizenBrew v2.0.5](https://github.com/reisxd/TizenBrew/blob/v2.0.5/tizenbrew-app/TizenBrew/tizenbrew-ui/src/pages/ModuleManager.jsx) probeert de module toe te voegen zodra het veld de focus verliest. Daarna opent het de modulelijst. De oorzaak van de gemelde invoer op de tv is nog onbevestigd.
- [ ] Reproduceer het probleem met **Modulebeheer → GitHub-module toevoegen**. Voer `ArcoMeerkerk/sendspin-cinema-tizen` in en druk op **Gereed**. Controleer of TizenBrew de volledige naam ontvangt en de tegel **Sendspin Cinema** toont.
- [ ] Herstel de invoerstap in TizenBrew als de naam verloren gaat. Controleer dat **Gereed** precies één keer de volledige naam verstuurt, dat lege invoer niets toevoegt en dat de gebruiker kan zien of de module is toegevoegd. Gebruik een testomgeving zodat de bestaande tegel op de tv beschikbaar blijft.

## 2. Verbinding, audio en weergave

- [x] Maak de Sendspin-poort instelbaar. De standaardpoort is `8927`. De test met `18927` en de controle op een ongeldige poort zijn geslaagd. Het adres op de vorm `host:poort` blijft invoerbaar.
- [x] Verhelp de gereproduceerde blokkade van de audio-uitvoer. Met een strenge autoplay-instelling stond de WebSocket open en bleef de oorspronkelijke `AudioContext` op `suspended`. In de nieuwe versie start **OK** de audio-uitvoer en produceert de testtoon meetbaar audio. De fysieke tv heeft nog een aparte controle nodig.
- [x] Test echte audio met Sendspin Go v1.8.2 in WSL. De Samsung TV Web Simulator speelde Opus vanaf `18927` af. Chromium speelde Opus op `8927` en FLAC op `18927` af. Een analyser mat in alle gevallen niet-stille samples. Dit was een lichte test zonder Home Assistant of Docker.
- [x] Gebruik vaste veldlabels en betere contrasten voor instellingen, titel, artiest en afspeeltijden. Vervang de schijf en de emoji-afspeelknoppen door een geluidssymbool en witte pictogrammen. De Nederlandse weergave is visueel beoordeeld.
- [x] Controleer de instellingen in alle zes ondersteunde talen en de Engelse fallback. Playwright bevestigde de weergave op 1280 × 720. De beelden staan in `playwright-720p-talen.png`.
- [ ] Bevestig het geluid op de fysieke Samsung-tv met Music Assistant en dezelfde radiozender.

## 3. Visueel controleren

**Status Samsung TV Simulator.** Sendspin Cinema draaide als zelfstandige webapp in Samsung TV Web Simulator 10.0.6 met een tv-viewport van 1920 × 1080. De Playwright-verbinding liep via de browser van de simulator.

- [x] Klik in de officiële simulator met `$playwright-cli` op de zichtbare knoppen **Omhoog**, **Omlaag**, **OK** en **Terug**. Focus verplaatsen, een ongeldige poort afwijzen, opslaan en de instellingen heropenen zijn geslaagd.
- [x] Bewaar simulatorbewijs in `Downloads/repo-screens/sendspin-cinema-tizen`. De bestanden `samsung-tv-simulator-instellingen-poort.png` en `samsung-tv-simulator-audio-en-iconen.png` tonen de aangepaste schermen.
- [x] Controleer de weergave op 1280 × 720. In Chromium past een lange titel op twee regels en blijft de artiestregel boven de afspeelknoppen. Zie `playwright-720p-lange-titel.png`.
- [x] Simuleer **Gereed** in de instellingen van Sendspin Cinema. Toetscode `65376` behield het IP-adres, de poort en de spelernaam en verplaatste de focus naar het volgende veld. Opslaan via **OK** op de virtuele afstandsbediening werkte.
- [ ] Controleer **Gereed** met het echte schermtoetsenbord op de Samsung-tv.
- [ ] Controleer modulebeheer in TizenBrew op een fysieke tv of met de officiële [Samsung TV Emulator](https://developer.samsung.com/smarttv/develop/getting-started/using-sdk/tv-emulator.html). TizenBrew 2.0.5 laadde zijn assets en `$WEBAPIS` niet in de Simulator. Het GitHub-invoerveld is daar niet getest.
