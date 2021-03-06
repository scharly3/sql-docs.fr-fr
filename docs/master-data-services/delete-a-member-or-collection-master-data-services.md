---
title: Supprimer un membre ou une collection (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 871a79fce70a7c37c32b9cbdae100cddd7bd0e80
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2018
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Supprimer un membre ou une collection (Master Data Services)
  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], supprimez un membre ou une collection lorsque vous n'en avez plus besoin. Si vous souhaitez supprimer des membres en bloc, utilisez plutôt les tables de mise en lots. Pour plus d’informations, consultez [Importer des données à partir de tables &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas supprimer un membre s'il est utilisé comme une valeur d'attribut basée sur un domaine pour un autre membre.  
  
## <a name="prerequisites"></a>Prerequisites  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
-   Pour les membres, vous devez au minimum disposer de l’autorisation **Supprimer** sur l’objet modèle feuille à partir duquel vous supprimez un membre.  
  
-   Pour les collections, vous devez avoir au minimum l'autorisation **Mettre à jour** sur l'objet modèle de collection feuille que vous supprimez.  
  
### <a name="to-delete-a-member-or-collection"></a>Pour supprimer un membre ou une collection  
  
1.  Dans la page d'accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste **Modèle** , sélectionnez un modèle.  
  
2.  Dans la liste **Version** , sélectionnez une version.  
  
3.  Cliquez sur **Explorateur**.  
  
4.  Pour supprimer les éléments suivants, procédez comme suit :  
  
    -   Pour un membre feuille, dans la barre de menus, pointez sur **Entités** , puis cliquez sur le nom de l'entité qui contient le membre.  
  
    -   Pour un membre consolidé, dans la barre de menus, pointez sur **Hiérarchies** , puis cliquez sur le nom de la hiérarchie qui contient le membre. Cliquez sur le nœud de la hiérarchie qui contient le membre.  
  
    -   Pour une collection, dans la barre de menus, pointez sur **Collections** , puis cliquez sur le nom de l'entité qui contient la collection.  
  
5.  Dans la grille, cliquez sur la ligne correspondant au membre ou à la collection à supprimer.  
  
6.  Cliquez sur **Supprimer un membre**, sur **Supprimer**ou sur **Supprimer une collection**.  
  
7.  Les administrateurs d’entité verront également apparaître une option de menu permettant de purger (supprimer définitivement) tous les membres supprimés de manière réversible dans la version d’entité.  
  
8.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
## <a name="see-also"></a> Voir aussi  
 [Réactiver un membre ou une collection &#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Membres &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Collections &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
  
