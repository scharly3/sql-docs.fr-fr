---
title: Définition du Mode de validation | Documents Microsoft
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45e975f0cb9ccc78a7cadd4f1a71b046528a9c10
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setting-the-commit-mode"></a>Définition du Mode de validation
Applications de spécifient le mode de transaction avec l’attribut de connexion SQL_ATTR_AUTOCOMMIT. Par défaut, les transactions ODBC sont en mode de validation automatique (à moins que **SQLSetConnectAttr** et **SQLSetConnectOption** ne sont pas pris en charge, ce qui est peu probable). Changement du mode de validation manuelle au mode de validation automatique automatiquement valide une transaction ouverte sur la connexion.
