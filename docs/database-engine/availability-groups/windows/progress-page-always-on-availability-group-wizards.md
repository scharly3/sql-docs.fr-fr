---
title: "Page Progression (Assistants de groupe de disponibilit&#233; Always On) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.failoverwizard.progress.f1"
  - "sql13.swb.adddatabasewizard.progress.f1"
  - "sql13.swb.addreplicawizard.progress.f1"
  - "sql13.swb.newagwizard.progress.f1"
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
caps.latest.revision: 13
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 13
---
# Page Progression (Assistants de groupe de disponibilit&#233; Always On)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilisez cette boîte de dialogue pour afficher la progression d'un Assistant [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] que vous exécutez dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. La barre de progression indique la progression relative des étapes que l'Assistant effectue.  
  
## Liste des éléments de l'interface utilisateur  
 **Plus de détails**  
 Cliquez sur la flèche bas pour afficher une grille de progression qui répertorie toutes les étapes effectuées, dans l'ordre, suivies de l'opération en cours actuelle. Cette grille comporte les colonnes suivantes :  
  
 **Nom**  
 Affiche une expression qui décrit une étape spécifique.  
  
 **État**  
 Indique le résultat des étapes terminées et le pourcentage d'exécution de l'étape active, comme suit :  
  
|Résultat|Description|  
|------------|-----------------|  
|**Erreur**|Indique que l'opération pour cette étape a rencontré une erreur. Cliquez sur le lien pour afficher une boîte de dialogue de message qui décrit l'erreur.|  
|**En cours (** *pourcentage-effectué* **)**|Indique que l'opération a maintenant lieu et estime le pourcentage de réalisation de cette étape.|  
|**Réussi**|Indique que l'opération pour cette étape s'est terminée avec succès.|  
  
 **Moins de détails**  
 Cliquez pour masquer la grille de progression.  
  
 **Annuler**  
 Cliquez pour ignorer les opérations restantes, puis quittez l'Assistant.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-database-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Basculer le groupe de disponibilité &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  