---
title: Détection de troncation de données activée à l’aide de ExtendedAnsiSQL | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 070537a00c0d179888260bc5cdcdfac0540f12dc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de troncation de données activée à l’aide de ExtendedAnsiSQL
Lorsque l’indicateur ExtendedAnsiSQL est activé et l’application insère des données dans un char ou une colonne binaire des données sont tronquées, la troncation est détectée. Lorsque l’indicateur ExtendedAnsiSQL est désactivée, les données sont tronquées sans avertissement, tel qu’il était dans les versions précédentes des pilotes ODBC bureau de base de données.
