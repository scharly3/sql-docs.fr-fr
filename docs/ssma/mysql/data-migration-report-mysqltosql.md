---
title: Rapport de Migration de données (MySQLToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5524a575-67dd-4ef6-9d17-3412df9b9f9c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 570a607c4521d78146143b048f5b5bc10033eedc
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="data-migration-report--mysqltosql"></a>Rapport de Migration de données (MySQLToSQL)
Le **rapport de Migration de données** boîte de dialogue s’affiche après la migration des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
## <a name="options"></a>Options  
**État**  
Indique l’état de la migration des données à partir de la source de la base de données cible.  
  
**De**  
La table source.  
  
**Pour**  
La table cible.  
  
**Nombre total de lignes**  
Le nombre de lignes de données dans la table source.  
  
**Nombre de lignes a été migrées**  
Le nombre de lignes de données migrés avec succès à la table cible.  
  
**Ratio**  
Le pourcentage de lignes migrés avec succès.  
  
**Détails**  
En cas d’échec de la migration des données, cliquez pour afficher les détails de la migration de la ligne sélectionnée dans le rapport. SSMA affichera la raison de l’échec.  
  
**Enregistrer le rapport**  
Enregistre le rapport à un. CSV, fichier (valeurs séparées par des virgules), qui peut être examiné à l’aide de Microsoft Excel.  
  
