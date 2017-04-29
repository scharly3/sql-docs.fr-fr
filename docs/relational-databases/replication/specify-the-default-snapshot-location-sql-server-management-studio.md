---
title: "Spécifier l’emplacement par défaut des instantanés (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6cda346b9dfdbc0a5693ce263456ee7f10076a2
ms.lasthandoff: 04/11/2017

---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>Spécifier l'emplacement par défaut des instantanés (SQL Server Management Studio)
  Spécifiez l'emplacement par défaut des instantanés dans la page **Dossier d'instantanés** de l'Assistant Configuration de la distribution. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md). Si vous créez une publication sur un serveur qui n'est pas configuré en tant que serveur de distribution, spécifiez un emplacement d'instantanés par défaut dans la page **Dossier d'instantanés** de l'Assistant Nouvelle publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Créer une publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Modifiez l’emplacement par défaut des instantanés dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>**. Pour plus d’informations, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Définissez le dossier d’instantanés pour chaque publication dans la boîte de dialogue **Propriétés de publication - \<Publication>**. Pour plus d'informations, voir [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>Pour modifier l'emplacement par défaut des instantanés  
  
1.  Dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>**, cliquez sur le bouton des propriétés (**…**) du serveur de publication pour lequel vous voulez modifier l’emplacement par défaut des instantanés.  
  
2.  Dans la boîte de dialogue **Propriétés du serveur de publication - \<Serveur de publication>**, entrez une valeur pour la propriété **Dossier des captures instantanées par défaut**.  
  
    > [!NOTE]  
    >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez spécifier un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  