---
title: "Importer une stratégie de gestion basée sur des stratégies | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a5cc4a64722d8c9533e7c0733cf6db18126f826e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="import-a-policy-based-management-policy"></a>Importer une stratégie de gestion basée sur des stratégies
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment importer une instance de stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour importer une instance de stratégie à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fourni avec des stratégies qui peuvent être utilisées pour contrôler une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, ces stratégies ne sont pas installées sur le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], mais elles peuvent être importées à partir de l’emplacement par défaut C:\Program Files\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 ou C:\Program Files (x86)\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 sur les installations 64 bits.
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Pour importer une instance de stratégie  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur le signe plus (+) pour développer le serveur où l’instance de stratégie importée résidera.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez avec le bouton droit sur le dossier **Stratégies** et sélectionnez **Importer une stratégie**.  
  
5.  Dans la boîte de dialogue **Importer** , tapez le nom et le chemin du fichier ou utilisez le bouton Parcourir (**...**) pour rechercher et sélectionner le fichier XML qui contient la stratégie. Pour plus d'informations sur les options disponibles dans la boîte de dialogue **Importer** , consultez [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
  
