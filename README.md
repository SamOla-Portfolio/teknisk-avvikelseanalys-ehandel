# teknisk-avvikelseanalys-ehandel

## 📌 Bakgrund och Syfte
Syftet med denna fallstudie är att förstå hur konsumenter använder webbplatsen, utvärdera användareffektivitet och identifiera var de kan gå vilse under köpprocessen. Projektet fokuserar särskilt på att definiera friktionen mellan olika enheter (dator och mobil) och besvara frågan: *"Vilka kanaler kan driva till faktiska och höga köpintentioner och hur kan detta optimeras?"*.

## 🛠 Teknisk Miljö och Datainsamling
Datainsamlingen och spårningen konfigurerades genom en tvärlinjersmetod:
*   **Google Analytics 4 (GA4):** Användes som demomiljö för att samla in data under 30 dagar (1 april till 1 maj 2026). Standardrapporter, utforskningar (Explorations) och trattrapporter (Funnel reports) användes för analys.
*   **Google Tag Manager (GTM) & GitHub:** En egenutvecklad webbsida på GitHub integrerades med GTM för att fungera som en testmiljö för händelsespårning.
*   **Integritet och GDPR:** Strikt samtyckeshantering (via Termly) implementerades, vilket krävde aktivering av avancerat samtyckesläge (Advanced Consent Mode) i GA4 för att hantera dataförlust när cookies nekas.

## 📊 Nyckeltal (KPI:er)
För att utvärdera trafik och kvalitet användes följande mätvärden:
*   **Volym:** Sessioner (med fokus på trafikförvärv).
*   **Kvalitet:** Engagemangsgrad (sessioner över 10 sekunder med minst två sidvisningar och en nyckelhändelse).
*   **Nyckelhändelser (Key Events):** `begin_checkout` och `purchase` för att mäta faktisk köpintention.

## 💡 Huvudsakliga Insikter
OTR-metoden (Observation, Tolkning, Rekommendation) tillämpades för att strukturera resultaten:

1.  **Hög trafikvolym men låg konvertering på mobila enheter:** Mobiltrafik driver fler sessioner än datorer, men har en betydligt lägre engagemangsgrad (15,02 % på mobil jämfört med 59,78 % på dator).
2.  **Organisk sökning är starkast:** Kanalen "Organic Shopping" driver den största konverteringsgraden oberoende av enhet, vilket indikerar stark varumärkeskännedom.
3.  **Teknisk friktion i e-postkanalen:** En extrem skillnad upptäcktes där e-postkanalen hade 1010 nyckelhändelser på dator, men endast 2 på mobil. Detta tyder på inkompatibilitet eller trasiga länkar i den mobila e-postklienten.
4.  **Kritiska datakvalitetsavvikelser i köptratten:** Trattanalysen (Funnel exploration) visade en orealistisk slutförandegrad på över 99,8 % mellan `begin_checkout` och `purchase`. Detta indikerar ett allvarligt spårningsfel i GTM vid det sista steget i utcheckningen.

## 🚀 Rekommenderade Åtgärder
Baserat på analysen rekommenderas följande datadrivna åtgärder för att garantera datakvalitet och minska friktion:
*   **Teknisk felsökning:** Verifiera GTM-systemet via `DebugView` och åtgärda spårningsfelet vid `purchase`-händelsen.
*   **A/B-testning:** Implementera tester på det mobila gränssnittet (särskilt kassasidorna) för att identifiera faktorer som leder till höga avbrottsfrekvenser (57,06 % vid `add_to_cart`).
*   **Omfördelning av budget:** Flytta marknadsföringsbudgeten till de kanaler som bevisat presterar bäst, såsom "Organic Shopping" och "Cross-network".
