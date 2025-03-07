1.  [[Digitale filters#wat zijn de verschillen tussen een digitale filter en een analoge filter|wat zijn de verschillen tussen een digitale filter en een analoge filter]]?
2.  [[Digitale filters#Wat wordt bedoeld met tijdsdomein binnen DSP|Wat wordt bedoeld met tijdsdomein binnen DSP]]?
3.       Welke responses bevat iedere lineaire filter?

4.       Wat is een recursieve filter?

5.       Hoe kan je de impulsresponsie van een recursieve filter vinden?

6.       Hoe kan informatie vervat zitten in het tijdsdomein?

7.       Hoe kan informatie vervat zitten in het frequentiedomein?

8.       Wat is het belang van stap- en frequentieresponsies?

9.       Welke stapresponse parameters zijn belangrijk voor digitaal filterontwerp? Noem deze en verklaar hun betekenis (verduidelijk telkens met een figuur)

10.   Welke parameters in het frequentiedomein geven weer hoe goed een filter is in het frequentiedomein?  Noem deze en verklaar deze beknopt.

12.   Waarom is de faseparameter van minder belang bij frequentiedomeintoepassingen?

13.   Stel dat je een frequentieresponse voor een filter hebt opgebouwd met 80 punten. Wat moet je doen opdat je hierop een FFT kan uitvoeren?

14.   Beschrijf hoe je een digitale HD-filter kan opbouwen vanuit LD-filter

15.  Beschrijf hoe je met een combinatie van LDF en HDF een bandsperfilter kan maken.

16.   Beschrijf hoe je een digitale banddoorlaatfilter (band pass) kan maken vanuit een bandsperfilter.

  

# Moving  Average filter

1.     Wat is de pricipiële werking van een moving average filter?

2.     Voor de eerste berekening(en) van een moving average filter zijn er geen waarden uit het verleden.  Hoe vermijd je best grote fouten tijdens het startmoment van de filter?   Verklaar je antwoord.

3.     Hoe bouw je een 5-punts (gewichten/factoren) moving average filter op?

4.     Waarvoor kan je een moving average filter het best voor gebruiken? Geef ook aan waarom de moving average filter hiervoor een goede oplossing is.

5.     Welke stappen (gebruik maken van functies) moet je doorlopen binnen scilab om een moving average filter te kunnen simuleren. Noem deze stappen/functies en verklaar beknopt hun doel.

6.      Met welke factor vermindert een 200 punt Moving Average Filter de ruis?

  

# Frequentieselectieve filters

1.     Vergelijk een FIR-filter met een IIR-filter. Wat zijn de voornaamste verschilpunten?

2.     Hoe wordt de transfertkarakteristiek van een digitaal systeem beschreven?

3.     Geef een voorbeeld van een FIR-verschilvergelijking.

4.     Geef een voorbeeld van een IIR-verschilvergelijking.

5.     Hoe kan je aan een versdhilvergerlijking zien dat de betreffende filter een FIR- of een IIR-filter is? 

6.     Welk zijn de eigenschappen van een digitale filter en omschrijf deze beknopt.

7.     Wat wordt bedoeld met genormaliseerde frequenties binnen DSP?  Waarom maakt men gebruik van genormaliseerde frequenties?

8.     Welke parameters heeft de wfir() – functie nodig om de filterparameters te kunnen bepalen van een digitale filter? Noem deze en omschrijf deze beknopt.

9.     Wat zijn de return-waarden van de functie wfir()?  Benoem deze em omschrijf deze beknopt.

10.  Geef en verklaar de kenmerken (voor/nadelen) van een rectangular window om te gebruiken als window voor een window-sync digitale filter.

11.  Geef en verklaar de kenmerken van een triangular window om te gebruiken als window voor een window-sync digitale filter.

12 . Geef en verklaar de kenmerken van een hamming window om te gebruiken als window voor een window-sync digitale filter.

13. Welke parameters heeft de iir() – functie nodig om de filterparameters te kunnen bepalen van een digitale iir-filter? Noem deze en omschrijf deze beknopt.

# Windowed-sync filters

1.       Welke parameters heeft de iir() – functie nodig om de filterparameters te kunnen bepalen van een digitale iir-filter?  Noem deze en omschrijf deze beknopt.

2.       Hoe ontwerp je een IIR-filter in scilab? (geef aan welke stappen je doorloopt)

3.       Hoe kan je de frequentieresponse van een IIR-filter weergeven in scilab?

4.       Wat zijn de kenmerken van windowed-sinc filters? (gebruik – nadeel – voordeel)

5.       Wat is de strategie van Windowed-sinc?

6.       Wat is een Blackman en Hamming window?  Waarvoor worden ze gebruikt en wat zijn hun onderlinge verschillen?

7.       Waarom wordt bij een windowed-sinc filter het afsnijpunt bepaald op het halve amplitudepunt in plaats van bij het -3dB punt?

8.       Welke stappen doorloop je tijdens het ontwerp van een windowed sync filter?

9.       Hoe kan je een windowed sync kernerl bestaande uit M = 62 punten aanpassen zodat door een FFT met 256 punten kan gebruikt worden?

10.   Een signaal is gesampled met een frequentie van 16 kHz.  Uit dit signaal wil men een frequentieband filteren met frequenties tussen 0 Hz en 800 Hz.  Men wenst een volledige onderdrukking voor frequenties die hoger zijn dan 1 kHz.

**Gevraagd** : bereken het aantal punten dat deze windowed-sinc kernel nodig heeft om deze filter te realiseren.

11.   Stel dat je een signaal hebt dat is gedigitaliseerd met een samplefrequentie van 8 kHz en dat je frequenties rond 1 kHz wil isoleren met een band tussen 940 Hz en 1060 Hz.  **Beschrijf** hoe je deze filter moet opbouwen.