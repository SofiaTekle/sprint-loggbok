# Individuell loggbok – Webbshop

## Inledande sammanfattning – arbete hittills

Hittills har vi tillsammans byggt en frontendapplikation som fungerar som en webbshop. Jag har bland annat skapat frontend-repot och lagt till CI för frontend. Jag har även arbetat med att visa produkter från backend och skapat en admin-sida med produktöversikt samt funktionalitet för att lägga till produkter. Dessutom har jag implementerat en produktdetaljsida som tar användaren till detaljvyn när man klickar på aktuell produkt. För att skydda privata sidor har jag implementerat protected routes så att en utloggad användare inte kan nå skyddade sidor.
Jag har också skapat en betalningslösning med Stripe på backend. Där har jag implementerat en Stripe Checkout Session, så att en användare kan genomföra ett köp, och en Stripe Webhook för att hantera händelser från Stripe och uppdatera orderinformation i databasen.

## Sprint 4 – vecka 42

### Vad jag arbetade med

- Denna vecka har jag skapat en gateway-applikation och tillhörande repo, konfigurerat nödvändiga filer och bjudit in gruppmedlemmar som collaborators.
- Jag har också implementerat autentiseringsflöden via gatewayen, med endpoints för inloggning och registrering som vidarebefordrar anrop till proxyservicen som i sin tur kommunicerar med auth-servern.
- Jag har testat flödet via Swagger och verifierat kommunikationen med auth-servern på Render samt att frontendapplikationen kan kommunicera med gateway-applikationen på Render.

### Eventuella problem och hur jag löste dem

- Jag tänkte att det skulle vara enklare att arbeta i separata filer, så jag skapade först en AuthGatewayService. Men jag upptäckte att den mest
  vidarebefordrade anrop till GatewayProxyService utan att tillföra egen logik. Jag valde att förenkla genom att låta AuthGatewayController anropa GatewayProxyService direkt och därmed undvika ett överflödigt lager i applikationen.
- En gruppmedlem uppmärksammade att vi skickade en orderbekräftelse via mejl utan att betalningen hade gått igenom. Jag tog på mig ansvaret för att lösa problemet eftersom jag hade tid över. Jag behövde kort sagt ändra flödet i Stripe Webhooken på backend så att betalningen går igenom först och att en orderbekräftelse skickas först efter att betalningen har genomförts.

### Samarbete och agilt arbete

- Det agila arbetet har fungerat bra. Vi har haft sprintplanering, daily scrums och retrospektiv för att planera veckans arbete, stämma av hur det går och se vad som kan förbättras. Kommunikationen i gruppen har också varit bra. Vi har kontakt i Teams-chatten flera gånger om dagen för att diskutera frågor och hjälpa varandra.
- Under den här veckan var arbetet lite annorlunda, det var lite svårare att dela upp arbetet i items och bestämma vem som skulle ansvara för vilka delar. Men vi löste det till slut.
- Under retrospektivet diskuterade vi att vi hade hoppat över två daily scrums under veckan, eftersom vi upplevde att kommunikationen i chatten fungerade bra. Vi kom ändå fram till att det är viktigt att försöka hålla fast vid våra planerade daily scrums. Även om chatten fungerar bra som kommunikation, så är daily scrums värdefulla eftersom det ger oss gemensam avstämning där vi kan berätta vad vi har gjort hittills, vad som återstår och lyfta hinder.
- Sammantaget har jag fått en bättre bild av hur agilt arbete fungerar. Det handlar inte bara om att dela upp arbetsuppgifter och utveckla funktioner, utan också om att kontinuerligt följa upp arbetet, samarbeta och anpassa arbetssättet.
