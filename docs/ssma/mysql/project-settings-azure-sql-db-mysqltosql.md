---
title: Paramètres (base de données SQL Azure) du projet (MySQLToSQL) | Documents Microsoft
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
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46dfaa1f7b35f87d13fc3a88fb00d6a26a1cf27f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>Paramètres (base de données SQL Azure) du projet (MySQLToSQL)
Les paramètres du projet SQL Azure vous permettent de configurer le suffixe de la base de données SQL Azure à ajouter dans la boîte de dialogue de connexion et permettent également à implémenter le mécanisme de pulsation dans la connexion à SQL Azure.  
  
Le volet SQL Azure est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue.  
  
-   Utilisez la boîte de dialogue Paramètres du projet pour définir les options de configuration pour le projet actuel. Pour accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **les paramètres de projet**, cliquez sur **général** en bas du volet gauche, puis **SQL Azure**.  
  
-   Utilisez la boîte de dialogue Paramètres du projet par défaut pour définir les options de configuration pour tous les projets. Pour accéder aux paramètres de SQL Azure, sur le **outils** menu, sélectionnez **DefaultProject paramètres**, sélectionnez le type de projet de migration SQL Azure à partir de **Version cible de la Migration** liste déroulante pour accéder aux paramètres dans le volet de SQL Azure, cliquez sur **général** en bas du volet gauche, puis **SQL Azure**.  
  
## <a name="options"></a>Options  
  
## <a name="connectivity"></a>Connectivité  
**Intervalle de pulsation**  
  
Spécifie un intervalle de temps à utiliser pour le mécanisme de pulsation afin de maintenir la connexion SQL Azure dans ' minutes : format des secondes.  
  
**Valeur par défaut**:' 4:45 '  
  
La valeur doit être spécifiée dans suis : format des ss (par exemple, ' 4:45 ' ou ' 0:50 ').  
  
**SQL Azure Server Suffix**  
  
Spécifie le suffixe du serveur SQL Azure  
  
**Valeur par défaut**: 'database.windows.net'.  
  
