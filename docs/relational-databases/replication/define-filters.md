---
title: "Définir les filtres | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4baa09c02936eb9e67bbcbcbf2b69d70253a4111
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="define-filters"></a>Définir les filtres
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La boîte de dialogue **Définir les filtres** vous permet de définir les filtres que vous appliquerez aux conflits de données afin d'afficher un sous-ensemble de conflits dans la grille. Pour définir un filtre, choisissez un opérateur dans la zone de liste déroulante **Opérateur** , puis entrez une valeur. Par exemple, pour afficher uniquement les conflits dans lesquels le perdant du conflit est le serveur **ReplTest1**, sélectionnez **Égal à** dans la zone de liste déroulante **Opérateur** et entrez **ReplTest1** dans la première colonne **Valeur** .  
  
## <a name="options"></a>Options  
 **Opérateur**  
 Sélectionnez un opérateur pour le filtre, ex. : **Inférieur ou Égal à**.  
  
 **Value**  
 Entrez une valeur pour le filtre. La plupart des opérateurs nécessitent uniquement la saisie d'une valeur dans la première colonne **Valeur** , mais les opérateurs **Entre** et **Non compris entre** nécessitent une valeur dans les deux colonnes **Valeur** .  
  
 **Désactiver**  
 Cliquez sur ce bouton pour effacer tous les filtres précédemment définis.  
  
## <a name="see-also"></a> Voir aussi  
 [Outil de résolution des conflits de réplication de Microsoft &#40;réplication de fusion&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Outil de résolution des conflits de réplication de Microsoft &#40;réplication transactionnelle&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
