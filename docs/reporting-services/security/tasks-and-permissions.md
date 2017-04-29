---
title: "T&#226;ches et autorisations | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "autorisations [Reporting Services], tâches"
  - "sécurité basée sur les rôles [Reporting Services], autorisations"
  - "security [Reporting Services], tasks"
  - "sécurité [Reporting Services], autorisations"
  - "sécurité basée sur les rôles [Reporting Services], tâches"
  - "tâches prédéfinies [Reporting Services]"
  - "tâches [Reporting Services]"
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
caps.latest.revision: 40
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 40
---
# T&#226;ches et autorisations
  Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les *tâches* correspondent aux actions qu’un utilisateur ou un administrateur peut effectuer. Les tâches sont prédéfinies. Vous ne pouvez pas créer de tâches personnalisées ou modifier celles qui sont fournies, par programme ou à l'aide d'un outil. Il en existe vingt cinq en tout. Ces tâches comprennent l'ensemble des opérations disponibles dans la sécurité basée sur l'attribution de rôles. Parmi ces tâches, citons par exemple « Afficher les rapports », « Gérer les rapports » et « Gérer les propriétés du serveur de rapports ».  
  
 Chaque tâche se compose d'un ensemble d'autorisations, qui sont également prédéfinies. Par exemple, la tâche « Gérer les dossiers » contient les autorisations de création et de suppression des dossiers, et d'affichage et de mise à jour des propriétés des dossiers. Les autorisations pour chaque tâche sont documentées pour fournir une description plus exacte de chaque tâche. Les utilisateurs n'interagissent pas directement avec les autorisations, ils ne les spécifient pas dans les attributions de rôle. Ils se voient accorder des autorisations indirectement par le biais des tâches qui sont incluses dans les définitions de rôles.  
  
 Ils peuvent effectuer les tâches uniquement si elles font partie d'un rôle et que celui-ci est compris dans une attribution. Ainsi, si la tâche « Consulter des modèles » n'est pas comprise dans un rôle, ou si le rôle ne fait pas partie d'une attribution, les utilisateurs ne peuvent pas consulter les modèles de rapports. Le diagramme suivant illustre comment les autorisations sont combinées en tâches, et comment les tâches sont combinées en rôles pouvant être utilisés dans des attributions de rôles spécifiques.  
  
 ![Diagramme Autorisations et tâches](../../reporting-services/security/media/report-securityobjects.gif "Diagramme Autorisations et tâches")  
Diagramme Autorisations et tâches  
  
## Tâches au niveau système et au niveau élément  
 Les tâches entrent dans deux catégories : niveau système et niveau élément. Un rôle ne peut inclure de tâches que d'une seule catégorie. Le tableau suivant décrit chaque catégorie de tâches.  
  
|Catégorie|Description|  
|--------------|-----------------|  
|[Tâches au niveau élément](../../reporting-services/security/item-level-tasks.md)|Actions qui sont effectuées sur des éléments gérés par un serveur de rapports, tels que les dossiers, les rapports, les modèles de rapports et les ressources.<br /><br /> Les tâches au niveau élément sont limitées à l'espace de noms de dossier du serveur de rapports. Tous les éléments auxquels vous accédez par le biais des dossiers sur un serveur de rapports ou par le biais de liens URL sont sécurisés par des attributions de rôles comprenant des tâches au niveau élément.|  
|[Tâches au niveau système](../../reporting-services/security/system-level-tasks.md)|Actions qui sont effectuées au niveau du système, telles que la gestion des travaux ou des planifications partagées pouvant être utilisées avec de nombreux éléments. Les tâches au niveau système sont limitées en dehors de l'espace de noms de dossier du serveur de rapports.|  
  
## Voir aussi  
 [Définitions de rôles](../../reporting-services/security/role-definitions.md)   
 [Predefined Roles](../../reporting-services/security/predefined-roles.md)   
 [Octroi d'autorisations sur un serveur de rapports en mode natif](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  