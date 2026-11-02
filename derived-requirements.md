# Afleiddar virknikröfur og samþykktarpróf

> Veljið tvær af [viðskiptareglunum](business-rules.md). Skráið eina sannreynanlega virknikröfu fyrir hvora reglu og tvö samþykktarpróf fyrir hvora kröfu. Endurnýta má viðeigandi virknikröfu úr fyrri vinnu með tilvísun í skráningarstað hennar.
>
> Sýnið tengslin **regla → ferli eða verkefni notanda → virknikrafa → samþykktarpróf** með auðkennum og tenglum í reitunum hér að neðan. Ekki þarf sérstaka rekjanleikatöflu. Tilgreinið viðbótarforsendur, t.d. um villuskilaboð eða atvikaskráningu. Próf mega aðeins krefjast hegðunar sem er tilgreind í kröfunni.

## VK-1 — Útreikningur stæðisgjalds

- **Viðskiptaregla: ** : [VR-1 - Útreikningur stæðisgjalds](business-rules.md)
- **Ferli eða verkefni notanda:** [UR-2.1 - Rétt upphæð fyrir rukkun](https://github.com/BaliVeselaj204/HBV301G-Verkefni1/blob/main/SRS/user_requirement.md#ur-21)
- **Virknikrafa:** Kerfið skal reikna greiðsluupphæð út frá skráðum komu- og brottfarartíma og gjaldskrá viðkomandi gjaldsvæðis. Ef dvöl nær yfir fleiri en eitt gjaldtímabil skal gjald hvers tímabils aðeins gilda fyrir þann hluta dvalarinnar sem fellur innan þess.
- **Viðbótarforsendur:** Í prófunum er gjald tekið fyrir hverja mínútu, án afslátta eða lágmarksgjalds. Tímasetningar eru á heilum mínútum og innan sama dags. Þetta eru forsendur fyrir prófin, en ekki staðfest gjaldskrá rekstraraðila.

### SP-1 — Dvöl innan eins gjaldtímabils

- **Sannreynir:** VK-1
- **Gefið:** Ökutæki hefur skráðan komutíma kl 10:00 og brottfarartíma kl 11:00. Gjald viðkomandi svæðis er 5 kr. á mínútu allan tímann.
- **Þegar:** Kerfið reiknar greiðsluupphæð fyrir dvölina.
- **Þá:** Greiðsluupphæðin er 300 kr.

### SP-2 — Dvöl yfir mörk gjaldtímabila

- **Sannreynir:** VK-1
- **Gefið:** Ökutæki hefur skráðan komutíma kl. 10:30 og brottfarartíma kl. 11:30. Gjald viðkomandi svæðis er 5 kr. á mínútu fyrir kl. 11:00 og 10 kr. á mínútu frá kl. 11:00.
- **Þegar:** Kerfið reiknar greiðsluupphæð fyrir dvöluna.
- **Þá:** Greiðsluupphæðin er 450 kr. : 150 kr. fyrir fyrri 30 mínúturnar og 300 kr. fyrir þær síðari.

## VK-2 — Vörn gegn tvíteknum greiðslubeiðnum

- **Viðskiptaregla:** [VR-2 - Ein greiðslubeiðni fyrir hverja dvöl](business-rules.md)
- **Ferli eða verkefni notanda:** [UR-2.2 - Sjálfvirk greiðslubeiðni eftir stæðistíma](https://github.com/BaliVeselaj204/HBV301G-Verkefni1/blob/main/SRS/user_requirement.md#ur-22)
- **Virknikrafa:** Við staðfesta brottför úr gjaldskyldri dvöl skal kerfið senda greiðslubeiðni til ytra greiðslukerfis. Endurtekin vinnsla brottfararatvika fyrir sömu dvöl skal ekki leiða til nýrrar greiðslubeiðni.
- **Viðbótarforsendur:** Hver dvöl hefur einstakt auðkenni. Ný heimsókn hjá sama ökutæki telst vera önnur dvöl. Í prófunum hefur brottför verið staðfest og gildar upplýsingar um notanda og útreiknaða greiðsluupphæð liggja fyrir.

### SP-3 — Fyrsta greiðslubeiðni fyrir dvöl

- **Sannreynir:** VK-2
- **Gefið:** Gjaldskyldri dvöl D-101 er lokið og brottför hefur verið staðfest. Engin greiðslubeiðni hefur verið send fyrir dvölina.
- **Þegar:** Kerfið fær upplýsingar um brottför úr dvöl D-101.
- **Þá:** Ein greiðslubeiðni fyrir D-101 er send til ytra greiðslukerfis.

### SP-4 — Endurtekin vinnsla af sömu brottför

- **Sannreynir:** VK-2
- **Gefið:** Ein greiðslubeiðni fyrir dvöl D-101 hefur þegar verið send og móttekin af ytra greiðslukerfi.
- **Þegar:** Kerfið fær aftur sömu upplýsingar um brottför úr dvöl D-101.
- **Þá:** Engin greiðslubeiðni er send til viðbótar til ytra greiðslukerfis fyrir dvöl D-101.
