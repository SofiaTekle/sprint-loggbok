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


## Sprint 5 – vecka 43

### Vad jag arbetade med

- Denna vecka har jag arbetat med JWT-cookie i gatewayn och frontend. Gatewayn sparar nu tokenen i en HttpOnly-cookie vid inloggning i stället för att tokenen hanteras och lagras på frontend. På frontend lade jag bland annat till credentials: "include" i anropen till gatewayn och tog bort lagring av tokenen samt Authorization-headern.
- Jag har även undersökt hur Playwright kan användas för att testa ett fullständigt flöde i en riktig webbläsare mot den faktiska backendmiljön. Jag skapade också ett test som omfattar inloggning och visning av produkter. 

### Eventuella problem och hur jag löste dem

- Denna vecka tog jag med min laptop till skolan och behövde därför klona ner projektet från GitHub. Jag fick problem med att köra projektet i IntelliJ och försökte felsöka det själv. Till slut frågade jag Håkan om hjälp, och han kom fram till att problemet låg i Maven Wrapper. Jag bytte till den vanliga Maven-installationen i stället, vilket löste problemet så att jag kunde fortsätta arbeta. 

### Samarbete och agilt arbete

- Sprintplaneringen och retrospektivet har fungerat som vanligt denna vecka. Under förra veckans retro kom vi fram till att vi skulle försöka hålla daily scrums tisdag till torsdag. Vi följde nästan planen, men missade tisdagen eftersom jag inte kunde delta då. Vi kommer att fortsätta sikta på daily scrums tisdag till torsdag nästa vecka.
- Samarbetet i gruppen fungerar även bra denna vecka. Det är enkelt och smidigt att arbeta tillsammans eftersom alla är engagerade och tar ansvar för sitt eget arbete. Alla bidrar aktivt till gruppens arbete, och om någon har en fråga eller behöver hjälp är alla villiga att hjälpa till.

