---
title: Mode de validation manuelle | Documents Microsoft
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
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d0e5a4cc5bbda6c8ee4414854f390694297c94e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="manual-commit-mode"></a>Mode de validation manuelle
*En mode de validation manuelle,* applications doivent terminer explicitement les transactions en appelant **SQLEndTran** pour les valider ou de les restaurer. C’est le mode de transaction normale pour la plupart des bases de données relationnelles.  
  
 Transactions dans ODBC n’ont pas à être initialisé explicitement. Au lieu de cela, une transaction commence implicitement à chaque démarrage de l’application fonctionne sur la base de données. Si la source de données requiert l’émission de la transaction explicite, le pilote doit le fournir chaque fois que l’application exécute une instruction qui requiert une transaction et il n’existe aucune transaction en cours.
