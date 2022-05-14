# Hej och välkommen till en SIR-baserad simulerad pandemi, där ett neuralt nätverk försöker begränsa smittspridningen!

För en beskrivning av hur simuleringsmodellen fungerar och vilka parametrar som finns, se avsnitt 2.1 *Modellteori* i slutrapport.pdf.

Det finns två olika versioner av programmet. Dessa är anpassade för olika ändamål och beskrivs nedan. Efter att dessa två varianter introducerats genomgås kort hur man gör för att köra en simulering i moln-tjänsten "Google Colab", där programmen återfinns.

Det första alternativet är SIR_graphic.ipynb. Denna version fungerar bra på att ge en visualisering av smittspridningen grafiskt. Den är bra om man vill se hur en simulation ser ut, men inte den bästa versionen för att dra slutsatser om hur olika parametrar påverkar smittspridningen. 

Det andra alternativet är SIR_resultgather.ipynb. Denna version har samma modularitet som grundmodellen, men visar inte upp en grafisk bild av samhället och agenterna. Detta leder till att den kör snabbare. Det finns också möjlighet att medelvärdesbilda över ett antal körningar med samma begynnelsevillkor, för att se till att det resultat man får inte bara var slumpmässigt bra eller dåligt. 

# Hur kör man programmen? 

När du bestämt dig för vilket program du vill köra så klickar du in på motsvarande länk i ovanstående stycken. Då omdirigeras du till Google Colab. Programmet är skrivet i blockform, och för att kunna göra simuleringar behöver det första kodblocket köras för att initialisera funktionerna som används.  Markera det första kodbocket och klicka sedan på knappen till vänster om kodblocket för att köra det.

Nedanför detta block finns ett formulär med ett antal reglage och kryssrutor som ställer in parametrarna för simuleringen. När parametrarna ställts in efter önskemål, klicka på knappen till vänster vid toppen av formulärsblocket. 

Den första inställningen är huruvida man vill göra en snabbstart med standardinställningarna. Då körs programmet med 800/5000 agenter i ett samhälle som är 40x40/100x100 rutor stort, beroende på om man kör det grafiska eller resultatsinsamlingsprogrammet.
30 agenter börjar som sjuka, och testkapaciteten är 30. Smittsannolikheten är 70%, sannolikheten för att bli frisk är 2% och risken att dö är 1%.

Vill man inte göra en körning med snabbinställningarna får man först ställa in vilken bekämpningsstrategi man vill ha. Det kan antingen vara ingen bekämpningsstrategi, eller så är PETER (det neurala nätverket) eller kontaktspårningsalgoritmen implementerade. 
Sedan ställer man in hur många agenter man vill ha, hur många test som ska finnas tillgängliga per tidssteg och huruvida testerna ska ha en sannolikhet att visa fel svar. 
Sedan bestäms sjukdomsparametrarna.

Därefter kommer man in på mer komplicerade funktionaliteter. 

Den första man kan ställa in är huruvida man vill implementera en samhällsnedstängning. Vill man det så får man klicka i rutan lockdown_activated för att aktivera det, och sedan specifiera starttid och längd av nedstängningen. 
Under nedstängningen så kommer agenternas förflyttningssannolikhet att vara sänkt från 80% till 10%.

Sedan kan åldersinställningar bestämmas. 
Vill man aktivera åldersinställningar får man först klicka i rutan age_activated. Åldersinställningarna sätter en viss andel av befolkningen till gamla, och ger dem en annourlunda dödssannolikhet.
Specifiera hur stor andel av befolkningen som klassas som gamla, och vad deras dössannolikhet ska vara. 

Därefter följer mutation. Mutation innebär att vid ett visst tidssteg så ändras sjukdomsparametrarna. 
Klicka i mutation_activated ifall det ska vara aktivt, specifiera sedan när mutationen ska inträffa och vad de nya sannolikheterna skall vara. 

Nedanför detta så kan inställningar för antalet samhällen bestämmas. Först väljs antalet samhällen till ett, två eller fyra. 
Sedan bestämmer man med vilken sannolikhet en agent ska kunna lämna sitt samhälle. 
Sist bestäms om det i startskedet skall vara uppdelat så att enbart ett samhälle börjar med sjuka individer, eller om det ska vara utspritt bland alla samhällen. 

Nästa inställning som görs är relaterat till befolkningskluster. Man ställer in om det ska vara aktiverat, och sedan hur många kluster man ska ha. När kluster är aktiverat så finns det en sannolikhet på 10% att en agent besöker ett kluster under ett tidssteg, innan den återgår till dess tidigare position. 

Kör man resultatsinsamlingsprogrammet så finns även möjlighet att spara datan. I sådana fall så specifieras vad namnet på den sparade filen skall vara. 
Datan kommer att sparas lokalt i mappen contents i Google Colab, och därifrån kan man ladda ner den. 
