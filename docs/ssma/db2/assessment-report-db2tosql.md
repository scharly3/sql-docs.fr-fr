---
title: Rapport d’évaluation (DB2ToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
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
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d4fb6816d4f9b99b21d0839195f756624f48da5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="assessment-report-db2tosql"></a>Rapport d’évaluation (DB2ToSQL)
La fenêtre de rapport d’évaluation affiche les résultats de la conversion d’objets de base de données à [!INCLUDE[tsql](../../includes/tsql_md.md)] syntaxe, et vous estimez la complexité et le coût de vos projets de migration.  
  
Pour accéder au rapport d’évaluation, sélectionner les objets à convertir dans l’Explorateur de métadonnées source, avec le bouton droit **schémas** ou **synonymes**, puis sélectionnez **créer un rapport**.  
  
## <a name="options"></a>Options  
  
|||  
|-|-|  
|Terme|Définition|  
|**Statistiques de conversion**|Affiche les statistiques de la conversion en type d’instruction. Ce volet est visible lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Objets par catégories**|Affiche le nombre d’objets par catégorie. Ce volet est visible uniquement lorsqu’un objet de groupe, tel qu’un schéma, ou un objet sans code est sélectionné dans le volet gauche.|  
|**Statistiques**|Affiche les statistiques de conversion de l’objet sélectionné. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche. Vous devrez peut-être développer **statistiques**, qui se trouve juste au-dessus du **Source** volet pour afficher ce volet.|  
|**Source**|Affiche le code de DB2 pour l’objet sélectionné et met en surbrillance le code qui n’a pas été converti à [!INCLUDE[tsql](../../includes/tsql_md.md)]. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour parcourir le code.|  
|**Cible**|Montre qui en résulte de la conversion [!INCLUDE[tsql](../../includes/tsql_md.md)] code de l’objet sélectionné et les messages d’erreur pour le code qui ne sont pas converties. Ce volet est visible uniquement quand un objet avec le code est sélectionné dans le volet gauche.<br /><br />Cliquez sur les numéros de ligne pour définir ou supprimer des signets. Utilisez les boutons en haut du volet pour parcourir le code.|  
|**Volet messages**|Affiche les erreurs, avertissements et messages d’information qui ont été générées lors de la création du rapport d’évaluation. Les messages sont regroupés par numéro. Pour afficher le code qui a provoqué l’erreur, cliquez sur **erreurs**, **avertissements**, ou **Info**, développez la catégorie de messages, puis cliquez sur un message.|  
  
