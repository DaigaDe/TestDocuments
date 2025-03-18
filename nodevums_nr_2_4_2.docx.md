

| A blue flag with yellow stars  Description automatically generated A black and red text with numbers  Description automatically generated |
| --- |
| Pētniecības projekts Nr. 2.4. “Daudzvalodīgs uzņēmuma informācijas semantiskās meklēšanas un atbilžu gatavošanas risinājums” |
| ID Nr.: 5.1.1.2.i.0/1/22/A/CFLA/008 |
| **2.4.2. Pētījums par kontekstā balstītu jautājumu atbildēšanu** |
|  |

| 2025, Rīga |
| --- |

**Informācija par dokumentu**

| Dokumenta numurs: | 2.4.2 |
| --- | --- |
| Dokumenta nosaukums: | Pētījums par lielajos valodas modeļos balstītu semantisko meklēšanu |
| Plānotais sagatavošanas datums: | 28.02.2025. |
| Faktiskais sagatavošanas datums: | 28.02.2025. |
| Galvenais autors: | Tilde SIA, Daiga Deksne, Mārcis Pinnis |
| Dalībnieki: | IT kompetences centrs, SIA (ITKC) |
| Pārbaudīja: | ITKC, Dr. Jānis Vucāns |
| Aktivitāte: | Pētījums par kontekstā balstītu jautājumu atbildēšanu |
| Pieejamība: | Konfidenciāls |
| Versija: | 1.0 |
| Atslēgas vārdi: | semantiskā meklēšana, lielie valodas modeļi, vektorizēšanas modeļi |

Zinātniskā virziena vadītājs Dr. Jānis Vucāns

Vadošais pētnieks Dr. Mārcis Pinnis

*Autortiesības © Tilde SIA, 2025*

*Visas tiesības aizsargātas. Šī dokumenta saturu vai tā daļas drīkst jebkādā veidā un nolūkā atveidot vai izplatīt pēc rakstiskas atļaujas saņemšanas no Tilde SIA.* 

*Turpmāk minētie produktu un uzņēmumu nosaukumi var būt to īpašnieku preču zīmes.*

*Sagatavots: Tilde, Vienības gatve 75A, Rīga, LV-1004, Latvija*

####
**Anotācija**

Šis dokuments apkopo pētniecības projekta “Daudzvalodīgs uzņēmuma informācijas semantiskās meklēšanas un atbilžu gatavošanas risinājums” aktivitātes “2.4.2. Pētījums par kontekstā balstītu jautājumu atbildēšanu” gaitu, rezultātus un galvenos secinājumus. Aktivitātē tika veikti eksperimenti ar uzvedņu modelēšanu dažādiem uzdevumiem, tostarp tulkošanai, tekstu klasificēšanai, SQL vaicājumu ģenerēšanai un informācijas izguvei. Tika analizētas lielo valodas modeļu, piemēram, GPT, Llama, Mistral, Gemma un Phi, spējas ģenerēt atbildes un tulkot starp angļu, latviešu, lietuviešu, igauņu un čehu valodām. Tāpat tika izveidota wiki datu kopa, kas ļāva testēt kontekstā balstītu atbilžu kvalitāti vairākās valodās. Pētījuma rezultāti sniedz salīdzinošu analīzi par dažādu lielo valodas modeļu efektivitāti un kvalitāti. Gan tulkošanas uzdevumam, gan atbildes ģenerēšanai visnoderīgākais ir OpenAI GPT-4o modelis, bet arī brīvpieejas modeļi, īpaši Gemma2:27b un Llama3.1:70b, uzrāda labus rezultātus pārbaudītajos NLP uzdevumos un valodās.

####
**Abstract**

This document summarizes the progress, results, and key conclusions of the research activity “2.4.2. Study on context-based question answering,” conducted as part of the project “Multilingual Enterprise Information Semantic Search and Answer Generation Solution.” The activity identified and developed methods applicable to context-based question answering. The activity involved conducting experiments with prompt modeling for various tasks, including translation, text classification, SQL query generation, and information retrieval. The capabilities of large language models such as GPT, Llama, Mistral, Gemma, and Phi were analyzed in generating responses and translating between English, Latvian, Lithuanian, Estonian, and Czech. Additionally, a wiki dataset was created to test the quality of context-based responses across multiple languages. The research results provide a comparative analysis of the efficiency and quality of different large language models. For both translation tasks and response generation, the most useful model is OpenAI's GPT-4o, while open-access models, particularly Gemma2:27b and Llama3.1:70b, also demonstrate strong performance in the tested NLP tasks and languages.

Saturs

[Saturs 5](#_Toc191629983)

[1 Ievads 6](#_Toc191629984)

[2 Termini un saīsinājumi 7](#_Toc191629985)

[3 Uzvedņu izmantošana atbilžu ģenerēšanā 8](#_Toc191629986)

[3.1 Uzvedņu lietojums un veidi 8](#_Toc191629987)

[3.2 RAG uzvednes ar ietvertu konteksta informāciju 9](#_Toc191629988)

[3.3 Jautājumu klasificēšanai izmantojamās uzvednes 9](#_Toc191629989)

[3.4 Uzvedne kopsavilkuma ģenerēšanai 10](#_Toc191629990)

[3.5 Uzvednes tabulāru datu izmantošanai 10](#_Toc191629991)

[4 Eksperimentos izmantotie lielie valodas modeļi 13](#_Toc191629992)

[5 Teksta tulkošana ar lielo valodas modeļu palīdzību 14](#_Toc191629993)

[6 Kontekstā balstītu atbilžu ģenerēšana dažādās valodās 18](#_Toc191629994)

[7 Dažādu lielo valodas modeļu atbilžu ģenerēšanas kvalitātes salīdzinājums 22](#_Toc191629995)

[7.1 Atbildes izvēle no vairākiem variantiem 22](#_Toc191629996)

[7.2 Atbildes ģenerēšana, izmantojot modeļa iekšējās zināšanas 23](#_Toc191629997)

[8 Secinājumi 26](#_Toc191629998)

[9 Izmantotās literatūras saraksts 27](#_Toc191629999)

1. Ievads

Kontekstā balstītas informācijas semantiskās meklēšanas un atbilžu ģenerēšanas sistēmas izveidei piemērota ir izguvē balstītas ģenerēšanas (RAG) pieeja, kas apvieno informācijas izgūšanas iespējas no zināšanu avotiem, kurus ir iespējams papildināt, ar lielo valodas modeļu (LLM) iespējām. LLM paļaujas uz iepriekš apgūtu zināšanu kopumu. RAG pieeja ļauj modeļiem dinamiski piekļūt ārējām datubāzēm, dokumentiem vai citām informācijas krātuvēm. Atbildes tiek veidotas, ņemot vērā ne tikai modeļa iekšējo zināšanu bāzi, bet arī reāllaikā iegūtu un kontekstam atbilstošu informāciju.

Mūsu mērķis ir uzlabot vienkāršoto RAG bāzes risinājumu, iekļaujot virkni jaunu metožu, kas ļauj risinājumam sasniegt labus rezultātus neatkarīgi no nozares un valodas, kādā ir konteksta dati un kādā lietotājs uzdod jautājumu.

1. aktivitātē tika pētītas metodes, kas saistītas ar jautājumam atbilstoša konteksta izguvi. 2. aktivitātē “Pētījums par kontekstā balstītu jautājumu atbildēšanu” tiek aplūkoti jautājumi, kas saistīti ar atbildes ģenerēšanu. Šajā aktivitātē tika izvirzīti šādi uzdevumi:

1. izpētīt un modelēt efektīvas vaicājumu uzvednes, lai nodrošinātu kontekstā balstītu atbilžu ģenerēšanu dažādās valodās;
2. izpētīt un izstrādāt metodes teksta tulkošanai ar lielo valodas modeļu palīdzību daudzvalodības iespējošanai;
3. izpētīt lielo valodas modeļu spējas ģenerēt dabiskās valodas atbildes dažādās valodās lietotāju vaicājumiem saistībā ar organizācijas darbību;
4. salīdzināt dažādu lielo valodas modeļu spējas ģenerēt atbildes iekšējo zināšanu mākslīgā intelekta sistēmas lietojumā.

Lai īstenotu šos uzdevumus, esam veikuši eksperimentus ar uzvedņu ģenerēšanu. Uzvednes eksperimentos tiek izmantotas dažādiem uzdevumiem – tulkošanai, tekstu klasificēšanai, SQL vaicājumu ģenerēšanai, informācijas vienību izguvei no teksta, atbildes ģenerēšanai saskaņā ar kontekstu. Esam pārbaudījuši lielo valodas modeļu tulkošanas iespējas dažādiem GPT, Llama, Mistral, Gemma un Phi modeļiem, tulkojot no angļu uz latviešu, lietuviešu, igauņu un čehu valodām un no šīm valodām uz angļu valodu. Esam izveidojuši *wiki* datu kopu, ar kuru ir pārbaudīta kontekstā balstītu atbilžu ģenerēšana angļu, latviešu, lietuviešu un igauņu valodās. Esam pārbaudījuši dažādu lokāli uzstādāmu brīvpieejas modeļu un komerciālo OpenAI modeļu kvalitāti.

Nodevums “Pētījums par kontekstā balstītu jautājumu atbildēšanu” ir sagatavots un izmantojams saskaņā ar projekta “Informācijas un komunikācijas tehnoloģiju kompetences centrs”, ID: 5.1.1.2.i.0/1/22/A/CFLA/008 pētniecības projektu Nr. 2.4 “Daudzvalodīgs uzņēmuma informācijas semantiskās meklēšanas un atbilžu gatavošanas risinājums”, kas tiek īstenots, izmantojot piesaistīto Atveseļošanas fonda līdzfinansējumu saskaņā ar 05.07.2022. MK noteikumiem Nr.418 Darbības programmas “Latvijas Atveseļošanas un noturības mehānisma plāna 5.1.r. reformu un investīciju virziena "Produktivitātes paaugstināšana caur investīciju apjoma palielināšanu P&A" 5.1.1.r. reformas "Inovāciju pārvaldība un privāto P&A investīciju motivācija" 5.1.1.2.i. investīcijas "Atbalsta instruments inovāciju klasteru attīstībai" īstenošanas noteikumi kompetences centru ietvaros” ietvaros.

1. Termini un saīsinājumi

Dokumentā lietoti specifiski termini, kuru detalizēts skaidrojums šajā dokumentā nav dots. Nereti šiem terminiem nav plaši lietota tulkojuma latviešu valodā, tāpēc, lai būtu vieglāk atrast atbilsmi starp šajā dokumentā lietotajiem latviešu valodas terminiem un izmantotajos avotos lietotajiem angļu valodas terminiem, šajā dokumentā ir iekļauts izmantoto terminu saraksts (skat. 1. tabulu) ar to tulkojumiem angļu valodā.

1. tabula. Izmantoto terminu un to tulkojumu saraksts

| **Termins angliski** | **Termins latviski** | **Saīsinājums** |
| --- | --- | --- |
| answer relevance | atbildes atbilstība |  |
| Bilingual Evaluation Understudy | divvalodu novērtējums | BLEU |
| Cross-lingual Optimized Metric for Evaluation of Translation | Interlingvāli optimizēta metrika tulkošanas vērtēšanai | COMET |
| context relevance | konteksta atbilstība |  |
| corpus | korpuss |  |
| cosine distance | kosinusa attālums |  |
| cosine similarity | kosinusa līdzība |  |
| character F-score | rakstzīmes F mērs | ChrF |
| faithfulness | uzticamība |  |
| keyword | atslēgvārds |  |
| large language model | lielais valodas modelis | LLM |
| Levenshtein distance | Levenšteina attālums |  |
| prompt | uzvedne |  |
| precision | precizitāte |  |
| recall | pārklājums |  |
| retrieval-augmented generation | izguvē balstīta ģenerēšana | RAG |
| Recall-Oriented Understudy for Gisting Evaluation | uz pārklājumu vērsta pamatpētījuma vērtēšana | ROUGE |
| Translation Edit Rate | tulkošanas kļūdu īpatsvars | TER |
| zero-shot prompt | bezpiemēru uzvedne |  |
| few-shot prompt | vairākpiemēru uzvedne |  |
| chain of thought | spriešanas ķēde |  |

1. Uzvedņu izmantošana atbilžu ģenerēšanā
   1. Uzvedņu lietojums un veidi

Izguvē balstītas ģenerēšanas pieejas otrajā solī (skatīt 1. attēlu), kas veic atbildes ģenerēšanu, svarīga loma ir uzvednes veidošanai. Uzvedne ir viss datu kopums, kas tiek padots ģeneratīvā valodas modeļa ievaddatos, uz kā pamata ģeneratīvais valodas modelis ģenerē atbildi (Schulhoff et al., 2024). Uzvedne sniedz norādījumus lielajam valodas modelim, kādai ir jābūt atbildei uz lietotāja uzdoto jautājumu. Lielie valodas modeļi ir jutīgi pret nelielām variācijām uzvedņu formulējumā, tādēļ problēmai atbilstošu uzvedņu ģenerēšana nav vienkāršs uzdevums. Ar uzvedni ir iespējams regulēt, kādai ir jābūt atbildes struktūrai, garumam un atbildes valodas stilam. Uzvednes tiek lietotas nevien RAG risinājumos, bet arī citu uzdevumu veikšanai, piemēram, kopsavilkumu ģenerēšanai, tulkošanai, klasificēšanai, vērtēšanai, programmu koda ģenerēšanai utt.


![](figures/0)


1. attēls. Semantiskā indeksēšana un izguvē balstītas ģenerēšanas divi soļi – dokumentu atrašana un (kontekstā balstīta) jautājumu atbildēšana

Uzvedņu izveidē tiek izmantoti dažādi paņēmieni. Ir bezpiemēru uzvednes, vairākpiemēru uzvednes, spriešanas ķēdes uzvednes, ar konteksta informāciju papildinātas uzvednes un citas (Sahoo et al., 2024). **Bezpiemēru uzvednēs** tiek ietvertas instrukcijas, bet nav piemēru, kas parāda, kādu atbildi LLM jāatgriež, ja ievadē ir konkrēti dati. Modelis tikai seko instrukcijām un izmanto zināšanas, kas ir pašā modelī (Radford et al., 2019). **Vairākpiemēru uzvednēs** ir ietverts viens vai vairāki piemēri ar sagaidāmajām atbildēm. Šāda informācija modelim palīdz labāk saprast uzdevumu, taču var arī izmainīt modeļa uzvedību, ģenerētajā atbildē dodot priekšroku biežāk sastaptiem vārdiem (Brown et al., 2020). **Spriešanas ķēdes uzvednēs** risināmais uzdevums tiek sadalīts sīkāk pa soļiem, aprakstot katru soli, kuru veicot noteiktā secībā, var nonākt pie vēlamā gala rezultāta (Wei et al., 2022).

* 1. RAG uzvednes ar ietvertu konteksta informāciju

Mūsu RAG risinājumā atbilde tiek ģenerēta, izmantojot šādu uzvedni angļu valodā (“{context\_str}” tiek aizvietots ar konteksta fragmentiem):

Answer ONLY with the facts listed in the provided context in question language. Your goal is to provide accurate and relevant answers based on the facts in the provided context. Avoid making assumptions or adding personal opinions. Emphasize the use of facts listed in the provided context documents. Avoid generating speculative or generalized information.

Context information is below.  
---------------------  
{context\_str}  
---------------------  
Instructions: Given the context information and chat history and without any other prior knowledge, answer the question.

If there is no answer found in context honestly answer with a single sentence: 'The context does not provide an answer to the question.'

Uzvedne detalizēti apraksta, kādai ir jābūt atbildei, kādu informāciju tajā drīkst izmantot, ko darīt, ja noderīgas informācijas kontekstā nav. Lai gan uzvedne ir angļu valodā, to var izmantot dažādām valodām. Uzvednē norādīts, ka atbildei uz jautājumu jābūt jautājuma valodā.

Uzvednes teksts var būt dažādās valodās. To var papildināt ar īpašām, konkrētam klientam specifiskām norādēm:

Tu esi uzņēmuma "X" virtuālā darbiniece Y. Lūdzu, sniedz īsas un latviski gramatiski korektas atbildes sieviešu dzimtē. Izvairies no 2. personas lietojuma daudzskaitlī un lieto darbības vārdus otrās personas vienskaitlī.

Atbildi draudzīgi, reaģējot ar neitrālām un īsām atbildēm uz elementārām saziņas frāzēm ārpus dotā konteksta. Piemēram, sasveicinoties (Uz sarunbiedra jautājumu 'Labdien' vai 'sveiki' - atbildi: 'Sveiki! Kā varu jums palīdzēt?'), atsveicinoties (uz redzēšanos, atā), un atbildi neitrāli, īsi uz ikdienas sarunvalodas frāzēm (piemēram, kā tu jūties, kā jums iet).

Atbildi uz jautājumiem par uzņēmumu un tā kontekstā, ja iespējams, sniedz piemērus un saites uz attēliem, mājaslapām un video. Rādi attēlus.

Lūdzu, atbildi, izmantojot informāciju, kas ir kontekstā vai ļoti tuvu tam pēc uzbūves un struktūras. Neizmanto valodas līdzekļus ārpus konteksta, uzturi kontekstā izmantoto valodas struktūru un līdzekļus. Īpaša uzmanība jāpievērš vārdiem, kas norāda uz laiku - šodien, vakar, aizvakar, rīt, parīt - noteikt, kāda nedēļas diena atbilst tam, kas ir norādīts nākamajā teikumā, un ģenerē atbildes par vajadzīgo nedēļas dienu. Ja kontekstā ir informācija, kurās dienās produkti ir pieejami, ņem to vērā. Ja lietotājs jautā par ievešanu, saproti to kā jautājumu par nodošanu.

Lūdzu, sniedz īsas un tiešas atbildes, koncentrējoties tikai uz uzdotajiem jautājumiem. Ja jautājums ir par cenu, maksu vai ievešanu un konkrētais produkts nav pieminēts kontekstā, atbildi, ka konteksts nesniedz atbildi.

* 1. Jautājumu klasificēšanai izmantojamās uzvednes

Ja zināšanu bāzē ir daudz dažādu failu par atšķirīgām tēmām, lietderīgi ir sašaurināt datu kopu, no kuras tiks izgūti jautājumam atbilstoši konteksta fragmenti. To var izdarīt, ar LLM palīdzību piešķirot lietotāja jautājumam kādu no iepriekš definētām kategorijām. Faili zināšanu bāzē arī tiek marķēti ar šīm kategorijām, tādēļ ir iespēja veikt filtrēšanu pirms jautājumam noderīga konteksta izguves. Klasificēšanas vairākpiemēru uzvednē ir pārskaitītas kategorijas, ir sniegti atslēgvārdu piemēri, kuri liecina par jautājuma piederību kategorijai, ir norādīts formāts, kādā atgriezt atbildi, ir norādīti vairāki piemēri ar jautājumiem un kādas kategorijas tiem piešķirt (“{question}” tiek aizvietots ar lietotāja jautājumu):

*You are an intelligent question classifier. Your task is to determine which category a user's question belongs to. The categories are:*

*1. BoilerMaintenance (examples: 'boiler', 'maintenance').*

*2. InsuranceServices (examples: 'insurance', 'payment safety').*

*3. ChimneyCleaning (examples: 'chimney', 'detector', 'cleaning').*

*4. OtherTopics (examples: 'dinamisk', 'stabil', 'invoice').*

*Your job is to analyze the question and respond in JSON format with the structure: `{"category": "<category>"}` Here `<category>` should be one of: 'BoilerMaintenance', 'InsuranceServices', 'ChimneyCleaning', or 'OtherTopics.'* 

*Examples: - Question: 'How does gas boiler maintenance work?' Answer: `{"category": "BoilerMaintenance"}`* 

*- Question: 'Is there insurance for chimney sweep services?' Answer: `{"category": "InsuranceServices"}`* 

*- Question: 'How do I clean a chimney?' Answer: `{"category": "ChimneyCleaning"}`* 

*- Question: 'What is the weather today?' Answer: `{"category": "OtherTopics"}`*

*User Question: "{question}"*

*Your Answer:*

* 1. Uzvedne kopsavilkuma ģenerēšanai

Lai ģenerētu faila kopsavilkumu, fails vispirms tiek sadalīts fragmentos. Tad katram fragmentam tiek ģenerēts kopsavilkums, izmantojot šādu uzvedni (“{chunk}” tiek aizvietots ar fragmenta tekstu):

*Here is the text fragment:*

*<fragment>*

*{chunk}*

*</fragment>*

*---------------------*

*Generate a concise summary for this text.*

Pēc tam fragmentu kopsavilkumi tiek sadalīti pa porcijām (fragmentu kopsavilkumu skaits vienā porcijā ir atkarīgs no LLM konteksta loga izmēra) un katrai no porcijām tiek ģenerēts kopsavilkums, izmantojot šo pašu uzvedni. Process iteratīvi tiek atkārtots, līdz tiek iegūts viens kopējs visa faila kopsavilkums. Šāds algoritms nodrošina to, ka informācija no katra faila fragmenta tiek atspoguļota arī kopējā faila kopsavilkumā.

* 1. Uzvednes tabulāru datu izmantošanai

Tabulāru datu izmantošana RAG risinājumā var radīt grūtības, ja tabulas datu izmērs pārsniedz pieļaujamo LLM konteksta loga izmēru un visa tabula neietilpst vienā fragmentā. Ir vajadzīga atšķirīga pieeja. Tabulārus datus optimālāk var izmantot, ja tie tiek iekļauti SQL datubāzē un ar SQL vaicājuma palīdzību tiek izgūtas lietotāja jautājumam atbilstošas datu rindas, ko var pievienot RAG uzvednei kā konteksta datus. Lai to īstenotu, var izmantot papildu uzvedni, ar kuras palīdzību vispirms no lietotāja jautājuma tiek ģenerēts SQL vaicājums (“{schema}” tiek aizvietots ar tabulas shēmu un “{question}” tiek aizvietots ar lietotāja jautājumu):

*SQL Database contains table whose schema we represent in the following JSON format. Table name is in "name" key, database type in "dbtype" key, and a list of field names and types in "fields" key. Some fields have restricted set of allowed values in "values" key.*

*Create the query to SQL Database for the user question, or return NONE if it is not possible to convert user question into query. The query must contain up to five fields related to user question. Use exactly the same field names as specified in the schema. include field in "" if it's name contains non-alphanumeric symbols.*

*For example, if you have table with the schema* 

*{'name': 'bernudarzi', 'fields': [{'name': 'name\_of\_educational\_institution', 'type': 'varchar'},{'name': 'address', 'type': 'varchar'},{'name': 'e-mail', 'type': 'varchar'},{'name': 'telephone', 'type': 'real'},{'name': 'manager', 'type': 'varchar'},{'name': 'language\_of\_study', 'type': 'varchar','values': ['latviešu','krievu','poļu','franču']},{'name': 'number\_of\_children', 'type': 'bigint}]} and client asks "which institutions have more than hundred children", you must return the following SQL query: "SELECT name\_of\_educational\_institution, number\_of\_children FROM bernudarzi WHERE number\_of\_children > 100"*

*For the fields with restricted values use only thouse words that are in the schema. For example, for the question "cik bērnu ir poļu bērnudārzā" generate SQL query "SELECT name\_of\_educational\_institution, number\_of\_children FROM bernudarzi WHERE language\_of\_study='poļu'".*

*The answer must always contain a valid SQL query or NONE if it is not possible to create a query from the user's question. Do not explain your answer. If necessary generate several queries separated by ';'. Avoid using UNION operator. Use LIKE operator with wildcards to filter by the text fields. When location is asked use address field with LIKE operator and wildcards.*

*SQL Database table schema: {schema}*

*User question: {question}*

*SQL query:*

Šī ir vairākpiemēru uzvedne, kurā dots tabulas shēmas paraugs, vairāki jautājumi un tiem atbilstoši SQL vaicājumu paraugi, kā arī ir norādīts, kādus SQL vaicājuma operatorus lietot vai nelietot.

Piedāvātā algoritma darbība tika pārbaudīta eksperimentāli. PostgreSQL datubāzē tika iekļauta tabula ar Latvijas pirmsskolas mācību iestāžu datiem (591 ieraksts). Tabulas lauki saturēja informāciju par iestādes nosaukumu, adresi, reģistrācijas numuru, vadītāju, e-pasta adresi, telefona numuru, apmācības valodu, izglītojamo skaitu. Tika izveidots saraksts ar 43 jautājumiem. Uz 40 jautājumiem ir iespējams pilnībā vai daļēji atbildēt, izmantojot tabulas datus. 3 jautājumi ir nesaistīti ar tabulas datiem. Jautājumi bija par izglītības iestāžu kontaktinformāciju, cik bērnu ir kādā izglītības iestādē, kurā izglītības iestādē ir vismazāk vai visvairāk bērnu, cik izglītības iestāžu ir kādā pilsētā, u.tml.

Izmantojot vairākpiemēru SQL vaicājuma uzvedni, ar OpenAI *gpt-35-turbo* un *gpt-4o* modeli tika ģenerēti jautājumiem atbilstoši vaicājumi. Eksperiments tika atkārtos arī ar bezpiemēru uzvedni (tā pati uzvedne, tikai izmesti abi jautājumu un tiem atbilstošo vaicājumu piemēri). *gpt-35-turbo* modelis ģenerēja vaicājumus gandrīz visiem jautājumiem, izņemot 3 jautājumiem, kas nav saistīti ar tabulas datiem. Pretstatā tam, *gpt-4o* modelis ģenerēja vaicājumus tikai tad, ja, izmantojot tabulas laukus, ir iespējams izgūt jautājumam atbilstošus datus. Piemēram, jautājumam “*Kurā pilsētā ir vairāk bērnudārzu – Kuldīgā vai Jelgavā?”* nav iespējams ģenerēt vaicājumu, kas atgriež ierakstus, jo tabulā nav lauka ‘Pilsēta’, pēc kura varētu grupēt un skaitīt ierakstus. Pilsētas nosaukums ir daļa no adreses lauka. Taču *gpt-35-turbo* modelis ģenerēja šādu vaicājumu, kuru izpildot, netiek atgriezts neviens ieraksts:

*SELECT address, COUNT(name\_of\_institution) FROM bernudarzi WHERE address LIKE '%Kuldīga%' OR address LIKE '%Jelgava%' GROUP BY address*

Atšķirīgi rezultāti tika iegūti, izmantojot vairākpiemēru un bezpiemēru uzvednes. Jautājumam “*Cik bērnu ir bērnudārzos, kas atrodas Ogrē?”* Ar vairākpiemēru uzvedni tika ģenerēts vaicājums, kas atgriež sarakstu ar visiem Ogres bērnudārziem:

*SELECT [Name of educational institution], [Number of children] FROM bernudarzi WHERE [Address] LIKE '%Ogre%'*

Ar bezpiemēra uzvedni tika ģenerēts vaicājums, kas atgriež bērnu skaitu Ogres bērnudārzos:

*SELECT SUM(number\_of\_children) FROM bernudarzi WHERE address LIKE '%Ogre%'*

Abi vaicājumi tika ģenerēti ar *gpt-4o*. Ar bezpiemēru uzvedņu ģenerētu vaicājumu atbilde uz jautājumu tiek iegūta uzreiz. Pat ja ar vairākpiemēru uzvedni uzreiz atbilde netiek iegūta, iekļaujot ierakstus par visiem Ogres bērnudārziem RAG uzvednes konteksta sadaļā un ģenerējot atbildi ar LLM, modelim ir pietiekami daudz informācijas, lai aprēķinātu vajadzīgo informāciju.

Eksperimentu rezultāti liecina, ka LLM spēj labi ģenerēt SQL vaicājumus un piedāvātā metode ir piemērota lielu tabulāru datu izmantošanai RAG risinājumos. Taču ir daži ierobežojumi. Informācijai, par kuru lietotājs gribētu uzzināt kādus statistiskus datus (piemēram, skaitu, salīdzināt mazāk vai vairāk, aprēķināt vidējo lielumu), ir jābūt laukos, pēc kuriem var grupēt. Piemēros pilsētas vārds nebija atsevišķā laukā. Turklāt jāņem vērā, ka brīvi uzdotā jautājumā lietotājs īpašvārdus var lietot kādā locījuma formā, kura var nesakrist ar īpašvārda formu tabulārajos datos.

1. Eksperimentos izmantotie lielie valodas modeļi

Daudzu lielo valodas modeļu izveidē ir izmantota tā pati *Transformer* arhitektūra ar paškontroles mehānismu. Atšķirības ir apmācības datu daudzumā, izmantoto parametru skaitā vai vektortelpu izmantojumā. *Hugging Face* platformā ir pieejami vairāk nekā 13 000 modeļi, kas ir izmantojami dažādās jomās un ir piemēroti dažādām valodām. Neraugoties uz šo daudzveidību, mazāk atbalstītajām valodām piemērotu modeļu skaits nav liels.

Eksperimentiem esam izvēlējušies populārākos modeļus, kuri būtu piemēroti arī valodām, kurās ir mazāk resursu, t.i., latviešu un lietuviešu valodai. Mēs salīdzinām gan komerciālos OpenAI modeļus, gan brīvpieejas modeļus (sk. 2. tabulu). Brīvpieejas modeļi tiek darbināti caur lokāli uzstādītu *Ollama*[[1]](#footnote-2) platformu, kas nodrošina datu privātumu.

2. tabula. Eksperimentos izmantotie daudzvalodu valodas modeļi (ar parametru skaitu miljardos iekavās)

| **Kategorija** | **GPT modeļi** | **Llama modeļi** | **Mistral modeļi** | **Gemma modeļi** | **Phi modeļi** |
| --- | --- | --- | --- | --- | --- |
| Autors | OpenAI | Meta | Mistral AI | Google | Microsoft |
| Testētie modeļi (parametri) | GPT-3.5.turbo-0125 (175b), GPT-4-0613, GPT-4o-2024-05-13 | Llama3 (8.03b), Llama3:70b (70.6b), Llama3.1 (8.03b), Llama3.1:70b (70.6b), Llama3.2 (3.21b) | Mistral-nemo:12b (12.2b) | Gemma2 (9.24b), Gemma2:27b (27.2b) | Phi3:3.8b (3.8b), Phi3:14b (14.0b) |

Papildus daudzvalodu modeļiem ir pārbaudīti arī divi vienvalodas lietuviešu valodas modeļi ***Lt-Llama2-7b-instruct****[[2]](#footnote-3)*un ***Lt-Llama2-13b-instruct****[[3]](#footnote-4)*. Tie ir apmācīti, izmantojot *Llama2* neironu tīkla arhitektūru, un ir paredzēti jautājumu atbildēšanas uzdevumam.

1. Teksta tulkošana ar lielo valodas modeļu palīdzību

Mašīntulkošana dabiskās valodas apstrādē ir uzdevums, kas fokusējas uz teksta automātisku pārveidi no vienas valodas citā. Mašīntulkošanas eksperimentiem tiek izmantota FLORES-200[[4]](#footnote-5) datu kopa, kurā ir ietverti paralēli teikumi vairāk nekā 200 valodās. Mēs izmantojam angļu valodu kā avota vai mērķa valodu, tulkojot no vai uz latviešu vai lietuviešu valodu. Tiek sagaidīts, ka rezultāti latviešu un lietuviešu valodai būs līdzīgi, jo abas valodas pieder vienai baltu valodu grupai. Salīdzināšanai mēs eksperimentos esam iekļāvuši igauņu valodu no somugru valodu grupas un čehu valodu, kas pieder slāvu valodu grupai. Mēs izmantojam *devtest* daļu no FLORES-200 datu kopas. Tajā ir 1012 paralēli teikumi.

Visos tulkošanas uzdevumos tiek izmantota šāda vienkārša uzvedne angļu valodā (“{text}” tiek aizvietots ar tulkojamo tekstu avotvalodā, “{lang\_a}” tiek aizvietots ar avotvalodu un “{lang\_b}” tiek aizvietots ar mērķvalodu):

{text}

Translate the above {lang\_a} text into {lang\_b}

Rezultātu vērtēšanai tiek izmantotas četras metrikas:

* **BLEU** ir mašīntulkošanā plaši izmantota metrika. Tā ir ātri un viegli aprēķināma un labi darbojas valodām ar līdzīgu vārdu secību. Šīs metodes trūkums ir pārmērīga paļaušanās uz n-grammu pārklājumu, ignorējot izteikuma jēgu. Tā slikti darbojas, vērtējot morfoloģiski bagātas valodas, jo pat neliela vārdu kārtības maiņa var būtiski ietekmēt vērtējumu, pat, ja tulkojums ir pareizs.
* **ChrF** metrika ir balstīta uz simbolu līmeņa precizitāti un pārklājumu. Tādēļ tā ir vairāk piemērota morfoloģiski bagātām valodām. Tās stiprā puse ir labāka vārdu locījumu formu vērtēšana salīdzinājumā ar BLEU. Tomēr ir arī trūkumi. Šīs metrikas rezultātus ir grūti skaidrot, simbolu līmeņa vērtējums dažkārt var piešķirt lielāku svaru līdzīgi rakstāmiem, bet pēc nozīmes nesaistītiem vārdiem.
* **TER** metrika vērtē darbību skaitu (teksta iespraušana, izmešana, maiņa, pārvietošana), kas nepieciešamas, lai mašīntulkotu tekstu pārveidotu references tulkojumā. Tā ir labi interpretējama, īpaši vērtējot pēcrediģēšanas scenārijus, jo atspoguļo, cik daudz pūļu nepieciešams, lai labotu tulkojumu. Tās trūkumi ietver jutības trūkumu pret sinonīmiju un teksta plūdumu. Tas nozīmē, ka tulkojums ar nedaudz atšķirīgu, bet pareizu izteikumu joprojām var saņemt sliktu vērtējumu.
* **COMET** ir moderna vērtēšanas metrika, kas izmanto ar cilvēka vērtējuma datiem apmācītus neironu tīkla modeļus. Tā spēj uztvert ne tikai vienkāršu vārdu sakritību, bet arī teksta semantisko nozīmi, padarot to tuvāku cilvēka vērtējumam. Tā ir piemērota tulkojumu vērtēšanai starp dažādiem valodu pāriem. Skaitļošanas ziņā COMET metrika ir dārga salīdzinājumā ar tradicionālajām metrikām. Ir vajadzīgs iepriekš apmācīts modelis. Šīs metrikas rezultātus nav iespējams interpretēt salīdzinājumā ar BLEU vai TER metrikām. Tāpēc to nevar izmantot, ja nepieciešams saprast, cik kvalitatīva ir konkrēta sistēma, tomēr tā ir piemērota, lai salīdzinātu divas dažādas mašīntulkošanas sistēmas, un secinātu, kura sistēma ļauj iegūt labākus tulkojumus.

Mašīntulkošanas eksperimenti tika veikti, salīdzinot standartizētus tulkojumus, kuros pieturzīmes, tukšumzīmes, pēdiņas, iekavas un citi simboli aizstāti ar atbilstošiem simboliem no ASCII tabulas. Tabulās atspoguļoti rezultāti, vērtējot ar BLEU (sk. 3. tabulu), ChrF (sk. 4. tabulu), TER (sk. 5. tabulu) un COMET (sk. 6. tabulu) metrikām.

3. tabula. BLEU rezultāti tulkojumiem ar dažādiem LLM

| **Tulkošanas virziens** | **gpt-3.5-turbo-0125** | **gpt-4o-2024-05-13** | **llama3** | **llama3:70b** | **llama3.1** | **llama3.1:70b** | **llama3.2** | **gemma2** | **gemma2:27b** | **mistral-nemo:12b** | **phi3:3.8b** | **phi3:14b** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en🡪cs | 32.37 | 37.12 | 19.01 | 28.49 | 17.92 | 28.44 | 13.69 | 25.13 | 30.12 | 19.82 | 0.25 | 7.78 |
| en🡪et | 26.59 | 31.69 | 9.11 | 19.19 | 6.68 | 17.91 | 4.97 | 16.00 | 20.21 | 11.35 | 0.13 | 1.98 |
| en🡪lt | 23.55 | 30.83 | 8.36 | 17.47 | 7.86 | 18.07 | 4.49 | 17.83 | 22.52 | 10.69 | 0.02 | 0.87 |
| en🡪lv | 25.89 | 35.58 | 8.76 | 19.29 | 6.89 | 19.32 | 3.94 | 17.87 | 24.11 | 11.74 | 0.01 | 0.02 |
| cs🡪en | 40.58 | 42.42 | 32.67 | 38.10 | 30.42 | 35.13 | 31.15 | 39.48 | 40.56 | 32.18 | 0.00 | 0.06 |
| et🡪en | 38.08 | 40.28 | 18.75 | 26.48 | 18.22 | 23.06 | 16.56 | 33.68 | 37.01 | 24.71 | 0.00 | 0.04 |
| lt🡪en | 32.99 | 36.37 | 19.17 | 24.67 | 17.94 | 23.76 | 16.66 | 32.92 | 33.65 | 23.41 | 0.00 | 0.04 |
| lv🡪en | 34.23 | 37.76 | 18.05 | 25.83 | 18.41 | 25.56 | 17.20 | 33.61 | 35.51 | 25.45 | 0.00 | 0.06 |

4. tabula. ChrF rezultāti tulkojumiem ar dažādiem LLM

| **Tulkošanas virziens** | **gpt-3.5-turbo-0125** | **gpt-4o-2024-05-13** | **llama3** | **llama3:70b** | **llama3.1** | **llama3.1:70b** | **llama3.2** | **gemma2** | **gemma2:27b** | **mistral-nemo:12b** | **phi3:3.8b** | **phi3:14b** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en🡪cs | 56.89 | 60.26 | 45.80 | 53.83 | 44.11 | 53.59 | 38.35 | 50.78 | 54.94 | 45.66 | 6.81 | 31.06 |
| en🡪et | 56.53 | 59.72 | 36.85 | 49.56 | 33.56 | 48.65 | 28.2 | 46.08 | 50.75 | 39.86 | 7.87 | 22.18 |
| en🡪lt | 52.22 | 58.18 | 35.90 | 47.08 | 34.46 | 47.73 | 27.92 | 46.71 | 51.43 | 38.62 | 6.84 | 15.50 |
| en🡪lv | 54.08 | 60.78 | 35.43 | 48.11 | 32.19 | 48.58 | 26.27 | 46.65 | 52.3 | 39.35 | 5.94 | 7.75 |
| cs🡪en | 65.14 | 66.56 | 58.64 | 62.91 | 56.66 | 60.60 | 57.25 | 63.84 | 64.51 | 58.14 | 4.11 | 6.38 |
| et🡪en | 63.10 | 64.82 | 45.42 | 52.34 | 43.74 | 49.09 | 42.05 | 59.10 | 61.91 | 51.60 | 3.62 | 7.05 |
| lt🡪en | 58.18 | 61.05 | 44.81 | 50.05 | 43.28 | 49.41 | 42.38 | 57.80 | 58.41 | 49.28 | 3.51 | 7.51 |
| lv🡪en | 60.94 | 63.83 | 45.28 | 52.33 | 44.39 | 51.34 | 43.92 | 59.03 | 60.71 | 52.23 | 3.30 | 7.16 |

5. tabula. TER rezultāti tulkojumiem ar dažādiem LLM

| **Tulkošanas virziens** | **gpt-3.5-turbo-0125** | **gpt-4o-2024-05-13** | **llama3** | **llama3:70b** | **llama3.1** | **llama3.1:70b** | **llama3.2** | **gemma2** | **gemma2:27b** | **mistral-nemo:12b** | **phi3:3.8b** | **phi3:14b** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en🡪cs | 55.02 | 51.03 | 69.53 | 59.16 | 73.46 | 59.75 | 78.18 | 62.92 | 57.37 | 68.69 | 117.55 | 89.47 |
| en🡪et | 61.54 | 57.45 | 85.84 | 70.65 | 98.47 | 72.79 | 97.37 | 73.45 | 67.65 | 81.02 | 127.14 | 107.35 |
| en🡪lt | 66.66 | 59.75 | 86.16 | 73.52 | 94.68 | 73.73 | 97.39 | 73.23 | 66.95 | 82.83 | 122.59 | 169.91 |
| en🡪lv | 62.07 | 54.16 | 83.84 | 69.35 | 92.97 | 70.13 | 96.24 | 70.48 | 63.08 | 79.37 | 115.73 | 185.80 |
| cs🡪en | 45.88 | 44.07 | 54.22 | 48.27 | 55.55 | 51.23 | 55.28 | 46.31 | 45.43 | 54.08 | 101.09 | 127.72 |
| et🡪en | 48.43 | 46.61 | 75.17 | 62.91 | 74.27 | 68.89 | 76.66 | 52.31 | 49.05 | 63.04 | 101.66 | 129.60 |
| lt🡪en | 55.27 | 51.95 | 73.14 | 64.70 | 73.46 | 66.40 | 75.14 | 54.33 | 53.47 | 65.73 | 101.51 | 133.21 |
| lv🡪en | 52.94 | 49.29 | 74.88 | 62.69 | 74.74 | 64.37 | 73.8 | 53.59 | 51.61 | 62.50 | 100.51 | 126.13 |

6. tabula. COMET rezultāti tulkojumiem ar dažādiem LLM

| **Tulkošanas virziens** | **gpt-3.5-turbo-0125** | **gpt-4o-2024-05-13** | **llama3** | **llama3:70b** | **llama3.1** | **llama3.1:70b** | **llama3.2** | **gemma2** | **gemma2:27b** | **mistral-nemo:12b** | **phi3:3.8b** | **phi3:14b** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en🡪cs | 0.91 | 0.92 | 0.81 | 0.90 | 0.82 | 0.90 | 0.66 | 0.89 | 0.91 | 0.84 | 0.25 | 0.51 |
| en🡪et | 0.92 | 0.92 | 0.65 | 0.86 | 0.63 | 0.87 | 0.48 | 0.84 | 0.89 | 0.75 | 0.27 | 0.37 |
| en🡪lt | 0.88 | 0.91 | 0.62 | 0.83 | 0.61 | 0.84 | 0.46 | 0.86 | 0.89 | 0.73 | 0.26 | 0.32 |
| en🡪lv | 0.88 | 0.91 | 0.59 | 0.82 | 0.58 | 0.83 | 0.44 | 0.83 | 0.88 | 0.72 | 0.25 | 0.27 |
| cs🡪en | 0.89 | 0.89 | 0.86 | 0.88 | 0.86 | 0.87 | 0.86 | 0.89 | 0.89 | 0.87 | 0.32 | 0.33 |
| et🡪en | 0.90 | 0.90 | 0.78 | 0.83 | 0.79 | 0.82 | 0.76 | 0.88 | 0.89 | 0.85 | 0.33 | 0.34 |
| lt🡪en | 0.86 | 0.88 | 0.77 | 0.81 | 0.77 | 0.82 | 0.75 | 0.87 | 0.87 | 0.82 | 0.32 | 0.34 |
| lv🡪en | 0.87 | 0.89 | 0.77 | 0.83 | 0.78 | 0.82 | 0.76 | 0.87 | 0.88 | 0.84 | 0.33 | 0.34 |

*GPT-4o* modelis uzrāda labākos rezultātus visiem tulkošanas virzieniem. Nākamā vietā var ierindot GPT*-3.5-turbo* vai *Gemma2:27b* modeli. Modeļi ar lielāku parametru skaitu (*Llama3:70b*, *Llama3.1:70b*, *Gemma2:27b*, un *Phi3:14b*) parasti uzrāda labākus rezultātus par tā paša tipa mazākiem modeļiem (*Llama3*, *Llama3.1*, *Gemma2*, un *Phi3.8*). Parametru skaits ir skatāms 2. tabulā. Tas, iespējams, saistīts ar to, ka lielāki modeļi labāk spēj saprast un apstrādāt sarežģītākas valodas konstrukcijas. Vērtējums tulkojumiem, kas iegūti ar *Phi* modeļiem, liecina par šo modeļu nepiemērotību lietuviešu, latviešu, igauņu un čehu valodai.

LLM modeļu spēja tulkot tika salīdzināta ar *DeepL*, kas ir neironu mašīntulkošanas sistēma, ko veidojis Vācijas uzņēmums DeepL GmbH. *DeepL* nereti pārspēj citas mašīntulkošanas sistēmas, piemēram, *Google Translate* un *Microsoft Translator*, īpaši valodas plūstamības un dabiskuma ziņā. *DeepL* izmanto dziļās mācīšanās metodes un lielu neironu tīklu, kas ir apmācīts ar daudzvalodu datiem. *DeepL* salīdzinājumā ar *GPT-4o* uzrāda labākus rezultātus, ja tiek tulkots no morfoloģiski vienkāršākām valodām uz morfoloģiski bagātākām valodām (sk. 7. tabulu). Savukārt tulkojot no morfoloģiski bagātākām valodām, *GPT-4o* ir vienādi vai labāki rezultāti. Atšķirība rezultātos gan ir minimāla. Jāatzīmē, ka *GPT-4o* nav īpaši apmācīts mašīntulkošanas uzdevumam.

7. tabula. COMET rezultātu salīdzinājums, tulkojot ar DeepL un GPT-4o

| **Tulkošanas virziens** | **GPT-4o** | **DeepL** | **Labāki rezultāti** |
| --- | --- | --- | --- |
| en🡪cs | 0.92 | 0.93 | deepL |
| en🡪et | 0.92 | 0.93 | deepL |
| en🡪lt | 0.91 | 0.92 | deepL |
| en🡪lv | 0.91 | 0.92 | deepL |
| cs🡪en | 0.89 | 0.89 | - |
| et🡪en | 0.90 | 0.90 | - |
| lt🡪en | 0.88 | 0.87 | gpt-4 |
| lv🡪en | 0.89 | 0.89 | - |

Visi iepriekšējie eksperimenti ar ne-GPT modeļiem tika veikti ar kvantētajām (4-bitu) versijām. Šādi modeļi ir mazāki izmēru ziņā un efektīvāki, tādēļ tos var darbināt uz iekārtām ar ierobežotu resursu pieejamību. Tomēr 4-bitu kvantēšana bieži vien tiek uzskatīta par pārāk agresīvu, īpaši uzdevumiem, kuriem ir svarīga augsta rezultātu precizitāte. Rezultāti, tulkojot ar nekvantētiem (16-bitu) modeļiem, ir skatāmi 8. tabulā.

8. tabula. COMET rezultāti, tulkojot ar nekvantētiem modeļiem (salīdzinājumā ar GPT-4o)

| **Tulkošanas virziens** | **GPT-4o** | **Llama3.1** | **Llama3.1:8b-instruct-fp16** | **Llama3.1:70b** | **Llama3.2** | **Llama3.2:3b-instruct-fp16** | **gemma2** | **gemma2:9b-instruct-fp16** | **gemma2:27b** | **Gemma2:27b-instruct-fp16** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en🡪cs | 0.92 | 0.82 | 0.86 | 0.90 | 0.66 | 0.68 | 0.89 | 0.90 | 0.91 | 0.91 |
| en🡪et | 0.92 | 0.63 | 0.74 | 0.87 | 0.48 | 0.50 | 0.84 | 0.86 | 0.89 | 0.89 |
| en🡪lt | 0.91 | 0.61 | 0.71 | 0.84 | 0.46 | 0.48 | 0.86 | 0.87 | 0.89 | 0.89 |
| en🡪lv | 0.91 | 0.58 | 0.69 | 0.83 | 0.44 | 0.46 | 0.83 | 0.84 | 0.88 | 0.89 |
| cs🡪en | 0.89 | 0.86 | 0.88 | 0.87 | 0.86 | 0.86 | 0.89 | 0.89 | 0.89 | 0.89 |
| et🡪en | 0.90 | 0.79 | 0.86 | 0.82 | 0.76 | 0.77 | 0.88 | 0.88 | 0.89 | 0.89 |
| lt🡪en | 0.88 | 0.77 | 0.84 | 0.82 | 0.75 | 0.76 | 0.87 | 0.87 | 0.87 | 0.87 |
| lv🡪en | 0.89 | 0.78 | 0.85 | 0.82 | 0.76 | 0.78 | 0.87 | 0.87 | 0.88 | 0.88 |

Nekvantētie modeļi sasniedz augstāku precizitāti nekā to kvantētās versijas. Tomēr neviens no tiem nepārspēj *GPT-4o* visiem valodu pāriem. Veiktspējas atšķirības starp nekvantētajiem modeļiem, piemēram, *Gemma2:27B* un *Llama3.1:70B*, salīdzinājumā ar *GPT-4o* ir vēl mazākas. Tas apstiprina iepriekš konstatēto, ka arī ne-GPT modeļi var būt efektīvi tulkošanas uzdevumos valodām, kurām pieejamo datu apjoms LLM apmācībai ir salīdzinoši mazs.

1. Kontekstā balstītu atbilžu ģenerēšana dažādās valodās

Turpinot 1. aktivitātē pētītās metodes, kas saistītas ar jautājumam atbilstoša konteksta izguvi, šajā aktivitātē mēs padziļināti pētām RAG procesa otro daļu – atbildes ģenerēšanu, balstoties uz konteksta informāciju, kas ir iekļauta uzvednē.

Šim mērķim mēs izmantojam daļu no [*rag-mini-wikipedia*](https://huggingface.co/datasets/rag-datasets/rag-mini-wikipedia) datu kopas. Daļā, ko mēs izmantojam, ir iekļauti 60 Vikipēdijas rakstu teksti un 794 unikāli jautājumi angļu valodā, kā arī īsas atbildes uz šiem jautājumiem un norāde uz failu, kurā atbilde ir atrodama. Šai datu kopai esam veikuši šādus papildinājumus:

1. failu teksts ir sadalīts fragmentos, fragmentiem ir ģenerēti vektori un ievietoti TypeSense vektoru datubāzē (vektori ģenerēti ar Hugging Face *paraphrase-multilingual-mpnet-base-v2* modeli);
2. ar OpenAI *GPT-4o* modeli ir identificēti faila fragmenti, kuros tieši atbilde ir atrodama (oriģinālajā marķējumā jautājumam ir piekārtots viss fails);
3. ar OpenAI *GPT-4o* modeli references atbildes ir izvērstas līdz pilnam teikumam;
4. ar OpenAI *GPT-4o* modeli jautājumi un izvērstās references atbildes ir pārtulkotas latviešu, lietuviešu un igauņu valodās.

Jautājumam atbilstošu failu fragmenti ir identificēti, izmantojot šādu uzvedni (“{n}” tiek aizvietots ar fragmentu skaitu failā un “{chunklist}” tiek aizvietots ar fragmentu masīvu):

Given a question and a list of text chunks, score the content of the chunks in 0 to 2 range.

0 - if chunk does not contain answer to the question,

1 - if chunk partly helps to answer the question,

2 - if chunk is highly relevant and holds answer to the question.

Do not repeat the text of the chunk, return only the list with numeric scores.

Here is the list of {n} text chunks:

{chunklist}

Here is the question:

LLM marķējums nav pilnībā korekts. Pārmarķējot manuāli 100 jautājumus, tika konstatētas 5 kļūdas. Visā datu kopā bija arī tādi jautājumi, kuriem LLM nebija varējis atrast atbilstošus fragmentus, t.i., visi faila fragmenti bija marķēti kā ‘*0*’. Šādi jautājumi tika manuāli laboti. Bija arī neskaidri gadījumi. Ir tādi jautājumi, uz kuriem nav skaidras atbildes failā, taču tie ir izsecināmi. Piemēram, uz jautājumu “*Vai Alesandro Volta bija ķīmijas profesors?*” references atbilde ir noliedzoša. Jautājumam atbilstošajā failā nekas nav teikts par to, ka Volta nebija ķīmijas profesors, bet ir informācija, ka viņš bija fizikas profesors. Šādām izsecināmām atbildēm tika ieviests jauns marķējums ‘*3*’. Kopumā marķējums ir manuāli mainīts 216 jautājumiem.

References atbildes ir izvērstas, izmantojot šādu uzvedni (“{q}” tiek aizvietots ar jautājumu un “{a}” tiek aizvietots ar īsu references atbildi):

Given the question and the short answer, expand the answer into a full sentence

Here is the question: {q}

Here is the short answer: {a}

Jautājumi un izvērstās references atbildes tiek tulkotas, izmantojot šādu sistēmas uzvedni (tulkojamais teksts tiek padots lielajam valodas modelim, izmantojot lietotāja uzvedni; tā satur tikai tulkojamo tekstu; līdzīgi ir arī lietuviešu un igauņu valodai):

Translate sentence into Latvian. Return just translated text without any explanation.

Papildinātajā datu kopā ir šāda informācija – fails, jautājums, īsā references atbilde, izvērstā references atbilde, jautājumam atbilstoši fragmenti, jautājums latviski, izvērstā references atbilde latviski, jautājums lietuviski, izvērstā references atbilde lietuviski, jautājums igauniski, izvērstā references atbilde igauniski (piemēru sk. 9. tabulā). Piemērā faila teksts ir dalīts astoņos fragmentos, no kuriem pirmais fragments ir marķēts kā atbildi saturošs, bet nākamie pieci fragmenti kā saistīti ar jautājumu.

9. tabula. Papildinātās *wiki* datu kopas ieraksta paraugs

| **Lauks** | **Vērtība** |
| --- | --- |
| fails | S10\_set3\_a4 |
| jautājums | Is Antwerp a city? |
| īsā references atbilde | Yes |
| izvērstā references atbilde | Yes, Antwerp is a city. |
| jautājumam atbilstoši fragmenti | [2, 1, 1, 1, 1, 1, 0, 0] |
| jautājums latviski | Vai Antverpene ir pilsēta? |
| izvērstā references atbilde latviski | Jā, Antverpene ir pilsēta. |
| jautājums lietuviski | Ar Antverpenas yra miestas? |
| izvērstā references atbilde lietuviski | Taip, Antverpenas yra miestas. |
| jautājums igauniski | Kas Antwerpen on linn? |
| izvērstā references atbilde igauniski | Jah, Antwerpen on linn. |

Literatūrā ir minēts, ka RAG risinājumu vērtēšanai var izmantot vairākas metrikas, kas balstītas gan uz tradicionālajām dabiskās valodas apstrādē lietotajām metrikām, piemēram, BLEU, ROUGE, F1, gan uz metrikām, kuras izmanto LLM. RAGEval (Zhou et al. 2024) izmanto tādas metrikas kā *completeness* ‘pilnīgums’, *hallucination* ‘halucinēšana’, *irrelevancy* ‘nesaistītība’, kuras tiek aprēķinātas, vispirms no references atbildes ar LLM izgūstot faktus un tad pārbaudot šo faktu esamību vai pretrunību ģenerētajā atbildē. Python bibliotēkā *Ragas* (Es et al. 2023) ietvertas gan tradicionālās metrikas, gan LLM balstītas metrikas. Metrika *faithfulness* ‘patiesums’ identificē faktus RAG risinājuma ģenerētajā atbildē un pārbauda, vai šie fakti ir izsecināmi no konteksta. Metrikas *response relevancy* ‘atbildes atbilstība’ aprēķinam ar LLM tiek ģenerēti RAG risinājuma ģenerētajai atbildei atbilstoši jautājumi, un šo jautājumu vektori tiek salīdzināti ar oriģinālo jautājumu. Platforma RagBench (Friel et al. 2024) RAG risinājumus vērtē, izmantojot šādas metrikas: *utilization* ‘izmantojums’, kas atspoguļo to, kāda daļa no konteksta tiek izmantota atbildes ģenerēšanai; *relevance* ‘noderība’, kas parāda, kāda daļa no konteksta vajadzīga jautājuma atbildēšanai; *adherence* ‘atbilstība’, kas identificē halucinācijas ģenerētajā atbildē; *completeness* ‘pilnīgums’, kas parāda, cik labi ģenerētā atbilde ietver derīgo konteksta informāciju. Pētījumā (Chen et al. 2024) tiek izveidota datu kopa RAG vērtēšanai, kurā tiek izmantotas šādas metrikas: *accuracy* ‘akurātums’, kura parāda, vai ģenerētā atbilde sakrīt ar references atbildi; *rejection rate* ‘noraidījuma mērs’ – šī metrika mēra LLM spēju ģenerēt noraidošu atbildi, ja tiek izmantots neatbilstošs konteksts, kurā atbildes nav; *error detection rate* ‘kļūdas noteikšanas mērs’ parāda, vai LLM spēj noteikt faktu kļūdas; *error correction rate* ‘kļūdas labošanas mērs’ parāda, vai LLM spēj labot kļūdu un atgriezt pareizu atbildi, ja noteikta faktu kļūda.

Mēs izmantojam šādas *Ragas* metrikas, kuru aprēķinam nav nepieciešams LLM:

* **BLEU** ir metrika, ko izmanto, lai vērtētu ģenerētās atbildes kvalitāti, salīdzinot to ar references atbildi. Līdzība starp ģenerēto atbildi un references atbildi tiek vērtēta, balstoties uz n-grammu precizitāti un piemērojot sodu tekstam, kas īsāks par references tekstu. Sākotnēji BLEU rādītājs tika izstrādāts mašīntulkošanas sistēmu vērtēšanai, taču to izmanto arī citos dabiskās valodas apstrādes uzdevumos. BLEU ir robežās no 0 līdz 1, kur 1 nozīmē pilnīgu atbilstību starp ģenerēto atbildi un references atbildi.
* **ROUGE** ir metriku kopums, ko izmanto, lai vērtētu ģenerētās atbildes kvalitāti, salīdzinot to ar references atbildi. Līdzība starp ģenerēto atbildi un references atbildi tiek vērtēta, balstoties uz n-grammu pārklājumu, precizitāti un F1 rādītāju. ROUGE ir robežās no 0 līdz 1, kur 1 nozīmē pilnīgu atbilstību starp ģenerēto atbildi un references atbildi.
* **Levenšteina attālums** aprēķina minimālo ievietošanas, dzēšanas un aizstāšanas operāciju skaitu, kas nepieciešams, lai vienu virkni pārveidotu par otru. Normalizēta Levenšteina attālums ir robežās no 0 līdz 1, kur 1 nozīmē pilnīgu atbilstību starp ģenerēto atbildi un references atbildi.
* **Semantiskā līdzība** tiek noteikta, aprēķinot kosinusa līdzību starp ģenerētās atbildes un references atbildes vektoriem, kas iegūti ar Hugging Face *paraphrase-multilingual-mpnet-base-v2[[5]](#footnote-6)* vektorizēšanas modeļa palīdzību. Līdzība ir robežās no 0 līdz 1, kur lielāka vērtība apzīmē augstāku semantisko līdzību starp ģenerēto atbildi un references atbildi.

Ir veikti vairāki atbilžu ģenerēšanas eksperimenti, dodot lielajam valodas modelim ar atšķirīgām metodēm izgūtu kontekstu – 1) fragmenti, kas izgūti no *TypeSense* vektoru datubāzes ar vektoru līdzības palīdzību, salīdzinot tos ar jautājuma vektoru; 2) fragmenti, kas izgūti gan ar vektoru līdzību, gan meklējot jautājumā sastopamos atslēgvārdus *TypeSense* datubāzē; 3) par kontekstu izmantojot failu, kurā ir atbilde uz jautājumu; 4) par kontekstu izmantojot faila fragmentus, kuri daļēji automātiski tika identificēti ar LLM palīdzību. Eksperimentu rezultāti redzami 10. tabulā. Visos eksperimentos konteksts ir oriģinālajā, angļu valodā.

Tā kā konteksts visos eksperimentos ir angļu valodā, var novērot, ka atslēgvārdu meklēšana papildus fragmentu izguvei uz vektoru līdzības pamata būtiskāk uzlabo rezultātus tikai angļu valodai. Atslēgvārdi tiek izgūti no uzdotā jautājuma valodas. Tātad atslēgvārdu izgūšanas metodi nav lietderīgi izmantot, ja konteksta valoda atšķiras no jautājuma valodas.

10. tabula. Atbilžu ģenerēšanas kvalitāte jautājumiem angļu (EN), latviešu (LV), lietuviešu (LT) un igauņu (ET) valodā

| **Valoda** | **Konteksta izguves metode** | | | **Metrikas** | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Vektoru līdzība** | **Atslēgvārdi** | **Fails** | **BLEU** | **ROUGE** | **Levenšteina attālums(izteikta kā līdzība)** | **Semantiskā līdzība** |
| EN | - | - | + | **0.5169** | **0.6712** | **0.6280** | **0.8467** |
| EN | - | - | pareizie fragmenti | 0.5020 | 0.6523 | 0.6192 | 0.8360 |
| EN | + | - | - | 0.4835 | 0.6239 | 0.6091 | 0.7805 |
| EN | + | + | - | 0.5124 | 0.6631 | 0.6327 | 0.8282 |
| LV | - | - | + | **0.2654** | 0.4764 | 0.4945 | 0.7692 |
| LV | - | - | pareizie fragmenti | 0.2597 | **0.4869** | **0.5067** | **0.7832** |
| LV | + | - | - | 0.2105 | 0.3690 | 0.4342 | 0.6176 |
| LV | + | + | - | 0.2173 | 0.3746 | 0.4419 | 0.6180 |
| LT | - | - | + | 0.2715 | 0.4916 | 0.5253 | 0.8024 |
| LT | - | - | pareizie fragmenti | **0.2807** | **0.4977** | **0.5325** | **0.8078** |
| LT | + | - | - | 0.2318 | 0.3912 | 0.4681 | 0.6542 |
| LT | + | + | - | 0.2341 | 0.3944 | 0.4655 | 0.6581 |
| ET | - | - | + | 0.2540 | 0.4688 | 0.4901 | 0.7723 |
| ET | - | - | pareizie fragmenti | **0.2699** | **0.4789** | **0.5024** | **0.7796** |
| ET | + | - | - | 0.2258 | 0.3787 | 0.4452 | 0.6263 |
| ET | + | + | - | 0.2312 | 0.3928 | 0.4566 | 0.6364 |

Metrikas, kuras izmanto LLM, šajos eksperimentos netiek izmantotas. Šo metriku trūkums ir mainīgā rezultātu ticamība. Dažādu LLM modeļu rezultāti var atšķirties. Modeļi mēdz neievērot instrukcijas uzvednē, piemēram, ja uzvednē ir teikts atgriezt rezultātus JSON formātā, modelis ne vienmēr to ievēro. LLM atbildes mēdz būt izsmeļošākas par references atbildēm. Piemēram, paplašinātā references atbilde uz jautājumu “*Where was Volta born?”* ‘Kur ir dzimis Volta?’ ir “*Volta was born in Como.”* ‘Volta ir dzimis Komo.’ Kontekstā balstīta LLM atbilde ir “*Volta was born in Como, Italy.”* ‘Volta ir dzimis Komo, Itālijā’. Šāda atbilde atbilst kontekstam, taču salīdzinājumā ar references atbildi tajā ir par vienu faktu vairāk, tādēļ LLM metrika šādu atbildi vērtē negatīvi, kaut gan cilvēkvērtējumā šāda atbilde būtu vērtējama pozitīvi.

Izmantojot OpenAI *GPT-4o* modeli caur Microsoft Azure platformu, ir ierobežojumi izsaukumu skaitam minūtē un apstrādāto vārddaļu skaitam minūtē, tādēļ šis modelis nav piemērots automātisku testu izpildei. Komerciālu modeļu izmantošana lielu testa datu kopu vērtēšanai ir ierobežota arī izmaksu dēļ.

1. Dažādu lielo valodas modeļu atbilžu ģenerēšanas kvalitātes salīdzinājums
   1. Atbildes izvēle no vairākiem variantiem

Atbildes izvēles uzdevumā modelim tiek dots jautājums ar vairākiem atbilžu variantiem. Modeļa uzdevums ir atgriezt pareizās atbildes identifikatoru. Šim uzdevumam mēs izmantojam divas datu kopas - Belebele[[6]](#footnote-7) un Klokan-QA. Belebele datu kopā ir iekļauti dati 122 valodās. Tajā ir 900 jautājumi, kas saistīti ar nelieliem teksta fragmentiem no FLORES-200 datu kopas. Jautājumi ir par 488 teksta fragmentiem. Katram jautājumam ir vairākas atbildes, no kurām tikai viena ir pareiza. Klokan-QA datu kopa ir čehu valodā. Klokan-QA datu kopā ir 4053 jautājumi no matemātikas olimpiādēm. Katram jautājumam ir pieci atbilžu varianti.

Šim uzdevumam tiek lietota bezpiemēru uzvedne angļu valodā (konteksts “{context}”, jautājums “{question}” un atbilde “{answer\_#}” ir kādā no eksperimentos izmantotajām valodām):

*This is the context: '{context}'. This is the question: '{question}'. Here are the 4 candidate answers: '1) {answer\_1}'; '2) {answer\_2}'; '3) {answer\_3}'; '4) {answer\_4}'. Report only the correct answer's ID (1, 2, 3, or 4) using the mandatory JSON format: {answer\_id: ""}.*

Rezultātu vērtēšanai tiek izmantota precizitātes metrika, kas raksturo pareizo atbilžu attiecību pret visām atbildēm. Katrs eksperiments tika veikts divas reizes ar katru valodas modeli. 11. tabulā atspoguļoti vidējie rezultāti no katra eksperimenta.

11. tabula. Atbildes izvēles uzdevuma precizitāte dažādiem valodas modeļiem un valodām

| **Datu kopa** | **valoda** | **gpt-3.5-turbo** | **gpt-4** | **gpt-4o** | **llama3** | **llama3:70b** | **llama3.1** | **llama3.1:70b** | **llama3.2** | **gemma2** | **gemma2:27b** | **mistral-nemo:12b** | **phi3:14b** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Belebele | en | 0.903 | 0.960 | 0.962 | 0.883 | 0.938 | 0.872 | 0.947 | 0.740 | 0.931 | 0.943 | 0.898 | 0.886 |
| cs | 0.818 | 0.928 | 0.937 | 0.769 | 0.888 | 0.743 | 0.892 | 0.676 | 0.907 | 0.910 | 0.800 | 0.296 |
| et | 0.773 | 0.920 | 0.928 | 0.576 | 0.770 | 0.560 | 0.821 | 0.397 | 0.859 | 0.893 | 0.686 | 0.003 |
| lt | 0.734 | 0.900 | 0.941 | 0.607 | 0.768 | 0.618 | 0.834 | 0.435 | 0.861 | 0.898 | 0.715 | 0.001 |
| lv | 0.756 | 0.929 | 0.950 | 0.571 | 0.710 | 0.581 | 0.783 | 0.410 | 0.869 | 0.914 | 0.689 | 0.002 |
| Klokan-QA | cs | 0.256 | 0.175 | 0.290 | 0.216 | 0.304 | 0.232 | 0.260 | 0.216 | 0.279 | 0.265 | 0.222 |  |

Rezultāti ir līdzīgi mašīntulkošanas uzdevuma rezultātiem. Visaugstāko precizitāti uzrāda *GPT-4o* un *GPT-4* modelis, kuriem seko *gemma* modeļi un *Llama3.1:70b*. Angļu valodai *Llama3.1:70b* ir nedaudz labāks par *Gemma2:27b*. *Phi* modelis ne-angļu valodām bieži vien vispār nespēja ģenerēt rezultātu JSON formātā.

Eksperimenti ar nekvantētiem modeļiem atspoguļoti 12. tabulā. Secinājumi ir līdzīgi – nekvantētiem modeļiem ir augstāka precizitāte, taču tā nepārsniedz *GPT-4o*.

12. tabula. Atbildes izvēles uzdevuma precizitāte dažādiem kvantētiem un nekvantētiem valodas modeļiem un valodām

| **Valoda** | **GPT-4o** | **Llama3.1** | **Llama3.1:8b-instruct-fp16** | **Llama3.1:70b** | **Llama3.1:70b-instruct-fp16** | **Llama3.2** | **Llama3.2:3b-instruct-fp16** | **Gemma2** | **gemma2:9b-instruct-fp16** | **gemma2:27b** | **Gemma2:27b-instruct-fp16** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| en | 0.960 | 0.872 | 0.910 | 0.947 | 0.956 | 0.740 | 0.725 | 0.931 | 0.932 | 0.943 | 0.939 |
| cs | 0.928 | 0.743 | 0.828 | 0.892 | 0.916 | 0.676 | 0.648 | 0.907 | 0.910 | 0.910 | 0.916 |
| et | 0.920 | 0.560 | 0.698 | 0.821 | 0.903 | 0.397 | 0.428 | 0.859 | 0.870 | 0.893 | 0.892 |
| lt | 0.900 | 0.618 | 0.731 | 0.834 | 0.892 | 0.435 | 0.463 | 0.861 | 0.886 | 0.898 | 0.892 |
| lv | 0.929 | 0.581 | 0.708 | 0.783 | 0.899 | 0.410 | 0.412 | 0.869 | 0.881 | 0.914 | 0.918 |

* 1. Atbildes ģenerēšana, izmantojot modeļa iekšējās zināšanas

Lai salīdzinātu dažādu modeļu ģenerētu atbilžu kvalitāti, tika sagatavoti 10 jautājumi latviešu un lietuviešu (sk. 13. tabulu) valodā par literatūru, vēsturi, loģiku un ģeogrāfiju.

13. tabula. 10 jautājumi latviešu un lietuviešu valodā

| **Latviski** | **Lietuviski** |
| --- | --- |
| Kas ir vienīgais no septiņiem senās pasaules brīnumiem, kas ir saglabājies līdz mūsdienām, un kur tas atrodas? | Koks vienintelis iš 7 senovės pasaulio stebuklų, išlikęs iki šių dienų ir kur jis randasi? |
| Kad sabruka Padomju Savienība, cik jaunas valstis tika izveidotas, un kā tās sauc? | Kada žlugo Sovietų Sąjunga, kiek naujų šalių atsirado ir kokie jų pavadinimai? |
| Kādi ir globālās sasilšanas galvenie cēloņi, un kādi pasākumi var mazināt tās ietekmi? | Kokios yra pagrindinės visuotinio atšilimo priežastys ir kokios priemonės galėtų sušvelninti jo poveikį? |
| Vai vari nosaukt vismaz vienu valodu no katras no šīm pirmvalodu grupām: baltu, slāvu, ģermāņu un somugru, un norādīt, kura valoda pieder kurai grupai? | Pateikite bent vieną kalbos, priklausančios kiekvienai iš baltų, slavų, germanų ir finougrų prokalbių, pavyzdį, nurodykite kuri kalba kuriai prokalbei priklauso. |
| Vai vari nosaukt mākslīgā intelekta definīciju? | Pateikite dirbtinio intelekto apibrėžimą |
| Pērtiķis, vāvere un putns sacenšas, kurš pirmais nonāks kokosriekstu koka virsotnē. Kurš pirmais sasniegs banānu? | Beždžionė, voverė ir paukštis bando pasiekti kokoso palmės viršūnę. Kuris pirmas nuskins bananą? |
| Kas ir augstākā virsotne Eiropā, un vai vari sniegt plašāku informāciju par tā atrašanās vietu, augstumu un nozīmi? | Koks yra aukščiausias kalnas Europoje? Pateikite išsamią informaciją apie jo vietą, aukštį ir reikšmę. |
| Kas ir fotosintēzes process, un kāpēc tas ir būtisks dzīvei uz zemes? | Kas yra fotosintezė ir kodėl šis procesas toks svarbus gyvybei Žemėje? |
| Ko vari pastāstīt par relativitātes teoriju? | Ką galite pasakyti apie reliatyvumo teoriją? |
| Kādas tēmas tiek apskatītas Džordža Orvela darbā “Dzīvnieku ferma” un kāpēc tās ir aktuālas arī mūsdienās? | Kokios temos gvildenamos Džordžo Orvelo „Gyvulių ūkis“ ir kodėl jos išlieka aktualios šiandien? |

Lielajiem valodas modeļiem tika dota vienkārša uzvedne jautājuma valodā, kas prasīja atbildēt uz jautājumu. Atbildes vērtēja divi latviešu un lietuviešu valodas eksperti. Tika vērtēti gramatiski nepareizi vārdi, nepareizas locījumu formas un izdomāti vārdi (vārdi, kādu valodā nav, bet kuri iederas valodas gramatiskajā sistēmā). Ja teikuma (vai frāzes) uzbūve neatbilda valodas normām, par kļūdainiem tika uzskatīti visi vārdi. Rezultāti latviešu valodai ir skatāmi 2. un 3. attēlā. Lietuviešu valodas rezultāti ir skatāmi 4. un 5. attēlā. Apzīmējums *const* reprezentē nepareizu sintaktisko konstrukciju skaitu, *err* apzīmē kļūdu skaitu (iekļaujot gramatikas kļūdas, nepareizas vārdu galotnes, nepareizi izvēlētus vārdus), *invent* apzīmē izgudrotu vārdu skaitu un *total* apzīmē visu kļūdu skaitu.

2. attēls. Vidējais kļūdu skaits starp 100 vārdiem latviešu valodā

3. attēls. Vidējais kļūdu skaits teikumā latviešu valodai

4. attēls. Vidējais kļūdu skaits starp 100 vārdiem lietuviešu valodā

5. attēls. Vidējais kļūdu skaits teikumā lietuviešu valodai

Kvalitatīvā analīze liecina, ka vislabākos rezultātus latviešu valodai uzrāda *GPT-4o* modelis. Šī modeļa ģenerētajos tekstos ir vismazāk valodai neatbilstošu sintaktisko konstrukciju un vismazāk gramatikas kļūdu. Lietuviešu valodai labāki par *GPT-4o* rezultātiem ir vienvalodas lietuviešu valodas modeļi *Lt-Llama2-7b-instruct* un *Lt-Llama2-13b-instruct*.

Šajā eksperimentā tika vērtēta arī atbilžu atbilstība jautājumam (sk. 14. tabulu).

14. tabula. Jautājumam atbilstošu atbilžu skaits

| **Modelis** | **Latviešu** | **Lietuviešu** |
| --- | --- | --- |
| llama3.1 | 3 (30%) | 2 (20%) |
| llama3.1:70b | 9 (90%) | 9 (90%) |
| gemma2:27b | 8 (80%) | 9 (90%) |
| gpt-4o | 10 (100%) | 9 (90%) |
| Lt-Llama2-7b-instruct | - | 5 (50%) |
| Lt-Llama2-13b-instruct | - | 4 (40%) |

Modeļu vērtējums valodas kļūdu ziņā ir līdzīgs atbilžu satura vērtējumam, izņemot vienvalodas lietuviešu valodas modeļus. Šie modeļi spēj ģenerēt lietuviešu valodas normām atbilstošu tekstu, taču nespēj adekvāti atbildēt uz jautājumiem. Šo modeļu spēja ievērot instrukcijas ir to trūkums. Jautājumu atbildēšanas uzdevumā nelielas gramatiskas vai strukturālas kļūdas ir pieļaujamas, ja vien ģenerētā informācija ir korekta.

Eksperimenta rezultāti liecina, ka kā alternatīvas komerciālajam *GPT-4o* modelim ir iespējams lietot kādu no brīvpieejas modeļiem - *gemma2:27b* vai *llama3.1:70b*.

1. Secinājumi

Pētījumā iegūtie rezultāti ļauj secināt, ka pētniecības projekta 2. aktivitātes mērķi ir sasniegti. Nozīmīga loma RAG risinājumā ir precīzu uzvedņu izmantošanai, kas sniedz lielajam valodas modelim norādījumus, kādam būtu jābūt ģenerētajam tekstam. Pētījuma ietvaros esam aplūkojuši dažāda veida uzvednes gan sarunas uzturēšanai, gan dažādu palīguzdevumu veikšanai – teksta tulkošanai, jautājumu klasificēšanai, kopsavilkuma veidošanai, SQL vaicājumu ģenerēšanai un citiem uzdevumiem. Šajā pētījumā veiktie salīdzinošie eksperimenti sniedz ieskatu dažādu lielo valodas modeļu teksta ģenerēšanas kvalitātē mašīntulkošanas, atbilžu izvēles un atbilžu ģenerēšanas uzdevumos, īpašu uzmanību pievēršot baltu valodām. Pētījumā ir iekļauta salīdzinoša analīze arī tādām mazāk atbalstītām valodām, kā igauņu (tulkošanas un kontekstā balstītas atbildes ģenerēšanas uzdevumam) un čehu (tulkošanas uzdevumam). Kontekstā balstītu atbilžu ģenerēšanas eksperimentos ir apzinātas metrikas (BLEU, ROUGE, Levenšteina attālums, vektoru semantiskā līdzība), ar kurām var vērtēt atbilžu ģenerēšanas kvalitāti. Ģenerēšanas kvalitātes vērtēšanai eksperimentos esam izvēlējušie metrikas, kas neizmanto LLM. Esam izpētījuši arī metriku grupu, kuras izmanto LLM. Šo metriku trūkums ir mainīgā rezultātu ticamība. Dažādu LLM modeļu rezultāti var atšķirties. Komerciālu modeļu izmantošana lielu testa datu kopu vērtēšanai ir ierobežota izmaksu dēļ.

Mašīntulkošanas eksperimentos tika pārbaudītas gan nekvantētas daudzvalodu modeļu versijas, gan šo modeļu kvantētas versijas. Abos gadījumos *GPT-4o* uzrādīja labākos rezultātus dažādām valodām. Lai gan *GPT-4o* nav īpaši trenēts mašīntulkošanas uzdevumiem, tomēr tā rezultātu kvalitāte ir tuva specializēto mašīntulkošanas pakalpojumu, piemēram, *DeepL*, kvalitātei.

Rezultāti rāda, ka arī brīvpieejas modeļi, īpaši *Gemma2:27b* un *Llama3.1:70b*, uzrāda labus rezultātus pārbaudītajos NLP uzdevumos un valodās. Šie modeļi labi darbojās ne tikai mašīntulkošanā un atbilžu variantu atlases uzdevumos, bet arī spēj ģenerēt tekstu bez kritiskām gramatikas un teksta uzbūves kļūdām. No tā var secināt, ka brīvpieejas modeļi ir pieņemama alternatīva, ja GPT modeļu izmantošana ir ierobežota privātuma apsvērumu dēļ vai izmaksu ierobežojumu dēļ.

1. Izmantotās literatūras saraksts

Brown, T., Mann, B., Ryder, N., Subbiah, M., Kaplan, J. D., Dhariwal, P., ... & Amodei, D. (2020). Language models are few-shot learners. *Advances in neural information processing systems*, 33, 1877-1901.

Chen, J., Lin, H., Han, X., & Sun, L. (2024, March). Benchmarking large language models in retrieval-augmented generation. In *Proceedings of the AAAI Conference on Artificial Intelligence* (Vol. 38, No. 16, pp. 17754-17762).

Es, S., James, J., Anke, L. E., & Schockaert, S. (2024, March). Ragas: Automated evaluation of retrieval augmented generation. In *Proceedings of the 18th Conference of the European Chapter of the Association for Computational Linguistics: System Demonstrations* (pp. 150-158).

Friel, R., Belyi, M., & Sanyal, A. (2024). Ragbench: Explainable benchmark for retrieval-augmented generation systems. *arXiv preprint arXiv:2407.11005*.

Radford, A., Wu, J., Child, R., Luan, D., Amodei, D., & Sutskever, I. (2019). Language models are unsupervised multitask learners. *OpenAI blog*, *1*(8), 9.

Sahoo, P., Singh, A. K., Saha, S., Jain, V., Mondal, S., & Chadha, A. (2024). A systematic survey of prompt engineering in large language models: Techniques and applications. *arXiv preprint arXiv:2402.07927*.

Schulhoff, S., Ilie, M., Balepur, N., Kahadze, K., Liu, A., Si, C., ... & Resnik, P. (2024). The prompt report: A systematic survey of prompting techniques. arXiv preprint arXiv:2406.06608.

Zhu, K., Luo, Y., Xu, D., Wang, R., Yu, S., Wang, S., ... & Sun, M. (2024). Rageval: Scenario specific rag evaluation dataset generation framework. *arXiv preprint arXiv:2408.01262*.

Wei, J., Wang, X., Schuurmans, D., Bosma, M., Xia, F., Chi, E., ... & Zhou, D. (2022). Chain-of-thought prompting elicits reasoning in large language models. *Advances in neural information processing systems*, 35, 24824-24837.

1. https://github.com/ollama/ollama [↑](#footnote-ref-2)
2. <https://huggingface.co/neurotechnology/Lt-Llama-2-7b-hf> [↑](#footnote-ref-3)
3. <https://huggingface.co/neurotechnology/Lt-Llama-2-13b-instruct-hf> [↑](#footnote-ref-4)
4. <https://github.com/facebookresearch/flores/tree/main/flores200> [↑](#footnote-ref-5)
5. https://huggingface.co/sentence-transformers/paraphrase-multilingual-mpnet-base-v2 [↑](#footnote-ref-6)
6. <https://github.com/facebookresearch/belebele?tab=readme-ov-file> [↑](#footnote-ref-7)