---
title: Le défilement par signet | Documents Microsoft
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
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a31cd92b18c3127ab6e6fb32ef83e640e064c13
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="scrolling-by-bookmark"></a>Le défilement par un signet
Lors de l’extraction des lignes avec **SQLFetchScroll**, une application peut utiliser un signet comme base pour la sélection de la ligne de début. Il s'agit d'une forme d'adressage absolu qui ne dépend pas de la position actuelle du curseur. Pour accéder à une ligne marquée par un signet, l’application appelle **SQLFetchScroll** avec un *FetchOrientation* de SQL_FETCH_BOOKMARK. Cette opération utilise le signet vers lequel pointé l’attribut d’instruction SQL_ATTR_FETCH_BOOKMARK_PTR. Elle retourne l'ensemble de lignes démarrant à la ligne identifiée par ce signet. Une application peut spécifier un décalage pour cette opération dans le *FetchOffset* argument de l’appel à **SQLFetchScroll**. Lorsqu’un offset est spécifié, la première ligne de l’ensemble de lignes retourné est déterminée en ajoutant le numéro de la *FetchOffset* argument pour le numéro de la ligne identifiée par le signet. Cette utilisation de la *FetchOffset* argument n’est pas pris en charge lorsqu’il est utilisé avec ODBC 2. *x* pilotes ; lorsqu’une application appelle **SQLFetchScroll** dans une API ODBC 2. *x* pilote avec *FetchOrientation* SQL_FETCH_BOOKMARK, la valeur du *FetchOffset* argument doit être défini à 0.
