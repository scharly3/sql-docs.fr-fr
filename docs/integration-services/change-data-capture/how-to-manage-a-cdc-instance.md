---
title: "Guide pratique pour gérer une instance CDC | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a243e7aaa5140a915c6eb13c04d0e00169c5c3c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-manage-a-cdc-instance"></a>How to Manage a CDC Instance
  Cette procédure décrit comment utiliser la console du concepteur CDC pour gérer les opérations d'instance de capture de données modifiées au moment de l'exécution.  
  
### <a name="to-manage-cdc-instance-operations"></a>Pour gérer les opérations d'instance de capture de données modifiées  
  
1.  Dans le menu **Démarrer** , sélectionnez **Console du concepteur de capture de données modifiées**.  
  
2.  Dans le volet gauche, développez **Capture de données modifiées** , puis le service qui contient l'instance que vous souhaitez afficher.  
  
3.  Sélectionnez le nom de l'instance à utiliser.  
  
4.  Dans le volet **Actions** à droite de la console du concepteur CDC, cliquez sur l'opération à effectuer.  
  
     Vous pouvez également cliquer avec le bouton droit sur le nom de l'instance dans le volet gauche et sélectionner l'opération à effectuer.  
  
     Vous pouvez effectuer les tâches suivantes :  
  
    -   **Démarrer**: pour démarrer la capture des modifications.  
  
    -   **Arrêter**: pour cesser de capturer des modifications.  
  
    -   **Réinitialiser**: cliquez sur **Réinitialiser** pour rétablir l’état (vide) initial de l’instance de capture de données modifiées. Cette option est disponible lorsque l'instance de capture de données modifiées est arrêtée. Toutes les modifications des tables de modifications et de l'état interne de l'instance de capture de données modifiées sont supprimées. Lorsque l'instance de capture de données modifiées est démarrée ultérieurement, la capture de modifications démarre à partir de ce point et inclut uniquement les transactions qui ont démarré après que l'instance de capture de données modifiées a démarré.  
  
    -   **Supprimer**: pour supprimer l'instance de capture de données modifiées.  
  
    -   **Script de journalisation Oracle** : cliquez sur ce lien pour afficher la boîte de dialogue du script de journalisation Oracle contenant le script de journalisation supplémentaire Oracle. Pour plus d'informations sur les opérations réalisables dans cette boîte de dialogue, consultez [Oracle Supplemental Logging Script](../../integration-services/change-data-capture/oracle-supplemental-logging-script.md).  
  
         **Remarque**: lorsque vous exécutez des scripts de journalisation supplémentaires, la boîte de dialogue des informations d'identification Oracle pour l'exécution de script s'ouvre et vous permet de spécifier un nom d'utilisateur et un mot de passe Oracle valides. Pour plus d'informations sur la façon de fournir les informations d'identification Oracle appropriées, consultez [Oracle Credentials for Running Script](../../integration-services/change-data-capture/oracle-credentials-for-running-script.md).  
  
    -   **Déploiement d'instance CDC**: pour générer un script de déploiement de l'instance de capture de données modifiées. Pour plus d'informations sur cette boîte de dialogue, consultez [CDC Instance Deployment Script](../../integration-services/change-data-capture/cdc-instance-deployment-script.md).  
  
     Pour plus d'informations sur ces tâches, consultez [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
 Vous pouvez également sélectionner **Propriétés** pour modifier les propriétés de configuration de l'instance de capture de données modifiées. Pour plus d'informations sur la modification des propriétés d'une instance de capture de données modifiées, consultez [Edit Instance Properties](../../integration-services/change-data-capture/edit-instance-properties.md).  
  
  
