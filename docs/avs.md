# Für AVS-Hersteller

## Inhaltsverzeichnis
- [PKV-Besonderheiten auf einen Blick](#pkv-besonderheiten-auf-einen-blick)
- [Umsetzungsthemen für AVS](#umsetzungsthemen-für-avs)
- [Spezifikationen & Dokumente](#spezifikationen--dokumente)
- [Weiterführende Informationen](#weiterführende-informationen)
- [Kontakt](#kontakt)

Dieser Bereich richtet sich an Hersteller von Apothekenverwaltungssystemen
(AVS) und bündelt die Informationen, die für die Anbindung und Umsetzung von
TI-Anwendungen für **Privatversicherte** relevant sind.

## PKV-Besonderheiten auf einen Blick
- Privatversicherte haben **keine elektronische Gesundheitskarte (eGK)** –
  TI-Anwendungen werden über ePA- und E-Rezept-App genutzt.
- Für den ePA-Zugriff wird die **KVNR** benötigt; zusätzlich berechtigt der
  Versicherte die Apotheke **aktiv per ePA-App**.
- Für Privatversicherte ist das E-Rezept **freiwillig**; das klassische
  Privatrezept bleibt jederzeit möglich.
 - Nach der Bezahlung erhalten Privatversicherte von der Apotheke eine digitale Apothekenrechnung (=Kostenbeleg) , Beispiel: https://github.com/DAV-ABDA/eRezept-Beispiele/blob/main/PKV/PZN_Mehrfachverordnung/PZN_MV_1/PZN_MV1_Kostenbeleg.pdf

## Umsetzungsthemen für AVS
- **ePA-Zugriff in der Apotheke:** Zugriff über Rezeptabruf oder Befugnis
  eines Stammkunden per ePA-App.
- **Annahme PKV-E-Rezept (WF200):** Umsetzung gemäß Implementierungsleitfaden
  Primärsysteme.
- **Apothekenrechnung (ehemals Kostenbeleg):** Abrechnung Privatversicherter
  gemäß TA DAV PKV. https://www.abda.de/themen/e-health/datenaustausch-pkv/

## Spezifikationen & Dokumente
- [Implementierungsleitfaden Primärsysteme E-Rezept (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_eRp/latest/)
- [Implementierungsleitfaden Primärsysteme ePA (gematik)](https://gemspec.gematik.de/docs/gemILF/gemILF_PS_ePA/latest/)
- [Technische Anlage PKV-Abgabedaten Apothekenrechnung (TA DAV PKV)](https://www.abda.de/fileadmin/user_upload/assets/ehealth/PKV_Datenauschtausch/TA_DAV_PKV_005_20250603.pdf)](https://www.abda.de/themen/e-health/datenaustausch-pkv/)
- [FHIR-Profile zum E-Abgabedatensatz](https://simplifier.net/erezeptabgabedaten)
- [FHIR-Profile zum PKV Abgabe-und Abrechnungsinformationen](https://simplifier.net/erezept-patientenrechnung/)

### Weiterführende Informationen
- [Linksammlung](https://github.com/NicoleEberhart/pkv-hersteller-portal/blob/main/docs/links.md) 
-	[Was Leistungsebringer zur ePA wissen müssen](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/was-leistunsgerbringer-zur-elektronischen-patientenakte-epa-wissen-muessen/)
-	[Leistungserbringer ermöglichen mit dem E-Rezept mehr Komfort für Privatversicherte](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/leistungserbringer-schaffen-mit-dem-e-rezept-mehr-komfort-fuer-privatversicherte/)
- [Online Check-in in der Praxis: Entdecken Sie den neuen Service für Ihre Privatversicherten](https://www.pkv.de/wissen/versorgung/digitale-medizin/informationen-fuer-aerzte/online-check-in-in-der-arztpraxis/)

## Kontakt
Bei Rückfragen wenden Sie sich an: ehealth-ti@pkv.de
