# skolschema

course *eller* subject används i Activity. Course för gymnasiet och annan verksamhet baserat på kurser (exempelvis komvux). Subject syftar på grundskoleämnen (är ju redundant för gymnasiet)

*Frågor:*

hostas schemat någonstans? URI / URL?

om "start" = "", är det invalid data eller?

Finns det en tjänst för att validera? Eric W?

comment på calendarevent, finns bättre namn? vad används den till?

Vi tycker exceptions är för komplicerade. Även om det kan beskrivas i källan, behöver det verkligen kommuniceras? En enklare variant vore att inte ha tid eller length, undantag betyder bara att "objektet" *inte* deltar? Resten borde handla om frånvaro snarare än schema? Om en elev ska gå litet tidigare på måndagar, skrivs det verkligen i schemat? Har vi nytta av detta?

Varför finns teachingLength för Group och Teacher men inte för elever?

Behövs flera parentactivity? Vi tycker inte det. NO-exemplet?

Courses och subjects på grupper. Kan det vara flera? Kan det vara både och?

activity.type sätter egentligen lärarens roll. behövs flera lärarroller i samma activity?

datumintervall som gått ur tiden ska väl inte behöva kommuniceras i evighet? Men hur får man då fram historisk data? Var går gränsen, eller hur avgränsar man?

Tjänstgöringsgrad - årsarbetstid är kanske bättre?

Var är man anställd? Skola? Kommun? Skolenhet? "Skola + skolform"?

Många frågor kring anställning. Olika antal timmar över tid?

Lärare hör inte till skolenhet, utan normalt sett till skola+skolform. I LifeCare kan man välja att koppla anställningen till en Skola eller till kommunen.

Skolenhet kopplar *bara* ihop elever och rektor.

Kommun
 Förvaltning
        anställning musik
  Skola 1
  Skola 2
     Skola 1 Sär
        anställning asdfsadf

Lärarroll på grupp? Klasslärare?


för grupper med olika typer, hur spärrar vi  olika typers attribut?

Employeegroup, oklart, ska den verkligen gruppera anställningar? Onödigt komplicerat och oklart syfte?

Course och subject ska väl också ha UUID om det är egna objekt och kan ha olika värdeförråd i skolformer, vissa helt fria.

behöver vi ha historik på årskurs?

Skolenhet / Skola på anställning, funkar det med ref till grupp?

Grupper kan väl inte ha skolform, bara elever?

Behövs flera responsible (ändring över tid?) för klasser?

Behövs flera kurskoder för en grupp?

Enklare att ha gruppmodell för skolor och skolenheter. Ibland kan skolan innehålla flera skolenheter, en det omvända borde kunna finnas, att flera skolor bildar en skolenhet.

Skolenhet, municipality code, gäller det även friskolor?
Skolenhet: vad är "ownerType"?


Ägare: hur gör vi? utökare meta-taggen?

Telefon i core-schemat, vi förutsätter att "mobile" innebär att det går att SMS:a. Det bör noteras i dokumentet?

schoolYear på grupp är inte optimalt, kan vi ta bort det? kanske?

nativelanguage? behövs det alls? i så fall på person-objektet.

student har vi problem med: årskurs program skolform är alla tidbundna. var är egentligen "student"objektet ? Tidigare har det *bara* innehållit kontaktpersoner.

student kopplas till activity både direkt och via studentassignment, varför? vad tillförs i studentassignment som gör att det behöver vara ett relationsobjekt?


Varför skola:
- schemaläggning avser just lokaler, dvs skola...
- lärare som jobbar på ett gymnasium med flera enheter så bestäms fördelningen i tjänstefördelningen, om alls. så var är läraren anställd?
- grupper som gäller flera skolenheter? egentligen tillhör *enbart* personer en enhet. grupperna tillhör ingen enhet, och bara utfallet av vilka elever som till slut fanns i gruppen ligger till grund för rapporteringen.


Employeegroup, är det verkligen något som finns och i så fall vad används det till?

2016-11-23
kan personnummer få vara globlat unikt?

kontaktpersoner har tappats bort i diagrammet, har alltid funnits i diskussionen och i det svartvita arket.

Pilarna från StudentAssignment och StudentException ska till User.

canonicalvalues på årskurs i enrolment och studengroup?

vi har hoppat fram och tillbaka med om elevgrupper behöver ha en lista med ämnen eller kurser som de är ämnade för. alltså om en studengrupp är skapade för att ha matematik, ska det listas, eller måste schemaprogrammet/schemaläggaren gissa det från namnet?



schoolunit.schoolTypeS


activity last changed finns i metadata.


daterange finns på många ställen...


i ativity: owner (skola eller enhet) och topic (ämne eller kurs)
notera att xxxAssigments "finns inte" riktigt...


calendarevent -> activity ska vara pil


scims group.member[type="Group"] är samma sak som vår parentGroup. dokumentera det?



studentexceptions -- hur förklara particitpates visavi de andra attributen?


employment: startDate och endDate istället för employmentTime... (och de är strängar...)

USer: securityMarking hellre än "protected"???

schoolyears (plural)  JA!
schoolTypes (plural)  "?"


display vs displayName  är inkonsekvent. även i SCIM-RFC:erna

CalendarEvent -> pilen till activity ska heta "activity"

resource oc room kan de verligen ägas av vilken grupp som helst eller är det bara school och schoolunit?

vi använder "resource" det gör även scim. Förvirring?



rektor är bortrefaktoriserat, men finns kvar i "SchoolUnit - Skolenhet
Klassen SchoolUnit är en specialisering av Grupp som används för att beskriva en Skolenhet med skolenhetskod och ansvarig rektor enligt Skolenhetsregistret.



---
2018-02-22

DELETE bör dokumenteras bättre. Ska användas för avregistrering, avliden mm. rätten att bli bortglömd också via DELETE.

ÄNDRING: mentorsskap blir en activityType istället för att ha en mentorsgrupp

--- fel i gamla exemplen:   "employmentRole": "Lärare",

Värdeförråd/kodregel för curriculum "LGR11"...


i curriculumReference:  "coursePlanCode": "", minns inte vad sjutton det är?

curriculumReference: gör ett "fullständigt exempel"

---
2018-03-20

organisation är underspecificerat.

enrolment för GY oklar. schoolYear har värdeförråd 0-10.

curriculum, värdeförråd? hur koda annars?

CurriculumReferenceInstance knepigt namn, kanske "kurs"?

lessonAttendanceLength olyckligt namn, bättre med det vi hade tidigare: attendanceLength.

 vi ändrade attendanceLength till ...Minutes.

aggreatedAttendance: behöver vi ta hänsyn till offiella aktiviteter? bara en aktivitet, korrekt? offeredSum är redundant? vad händer om de inte summerar?

grantedTimestamp / reportedTimestamp
code_GradeCorrection?


värdeförråd för betyg? inte för alla, men i texten? SVAR: Framför dokumentera i allt i texten. (Kolla YH.) avsaknad av betyg ska också beskrivas ("3")
notering (titel o innehåll) för betyg, underliga?
remark vs notes?

-------

Till nästa gång:

Engelska för enstaka kurser


---

code_SchoolYear 0, 1, 2 .. 10.

semester vs final grade?

språkkoder för betyg?

aktivitets endDate bör kunna vara öppet. kanske inte? om förskolan ska in där kan det vara rimilgt...?

behöver vi beskriva vilken avdelning personal i förskolan jobbar med? vi tror att det inte behövs eftersom personalen flyttar mellan avdelningar efter behov.

"Omsorg" för aktivitetsgrupp (jfr mentorskap). används mentorskap på förskolan?

Avdelning på studentGroup, OK?

Modellen kring närvaro på förskolan bör synkas med flera.

LeaveOfAbsence, behövs request/boolean eller motsvarande om det är godkänt eller önskat.
