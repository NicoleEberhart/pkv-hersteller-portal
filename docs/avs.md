# Für AVS-Hersteller

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

## Umsetzungsthemen für AVS
- **ePA-Zugriff in der Apotheke:** Zugriff über Rezeptabruf oder Befugnis
  eines Stammkunden per ePA-App.
- **Elektronische Medikationsliste:** Umsetzung der Medikationsliste im
  ePA-Aktenkonto (FHIR); optional ein systemgestützter AMTS-Check.
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

## Kontakt
Bei Rückfragen zur AVS-Anbindung: ehealth-ti@pkv.de
