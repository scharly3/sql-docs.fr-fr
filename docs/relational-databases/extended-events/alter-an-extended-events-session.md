---
title: "Modifier une session d&#39;&#233;v&#233;nements &#233;tendus | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
  - "xevents"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 9
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 9
---
# Modifier une session d&#39;&#233;v&#233;nements &#233;tendus
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Après avoir créé une session d'événements étendus, vous pouvez la modifier en fonction de vos besoins à l'aide de l' **Assistant Événements étendus SQL Server**.  
  
## Avant de commencer  
 Vous ne pouvez pas modifier une cible pour les sessions actives et inactives, et vous ne pouvez pas modifier les configurations avancées de propriétés pour une session active.  
  
 Vous pouvez apporter les modifications suivantes aux sessions d'événements actives et inactives :  
  
-   Ajouter ou supprimer des événements de la session, puis modifier les configurations des événements, telles que les champs d'événement, les filtres et les actions.  
  
-   Ajouter ou supprimer une cible de la session d'événements.  
  
-   Activer l'option **Démarrer la session d'événements au démarrage du serveur** .  
  
 Vous pouvez apporter les modifications supplémentaires suivantes à une session d'événements inactive :  
  
-   Activer l'option **Suivre la relation entre les événements** .  
  
-   Modifier la configuration de propriétés avancée.  
  
> [!NOTE]  
>  L’**Assistant Événements étendus SQL Server** ne prend pas en charge la modification de la session d’événements.  
  
## Comment modifier une session d'événements étendus à l'aide de l'Assistant Événements étendus SQL Server  
  
-   Dans l'Explorateur d'objets, développez **Gestion**, **Événements étendus**, puis **Sessions**.  
  
-   Cliquez avec le bouton droit sur la session à modifier, puis cliquez sur **Propriétés**.  
  
-   Dans la boîte de dialogue **Propriétés** , apportez les modifications appropriées, puis cliquez sur **OK**.  
  
## Voir aussi  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Créer une session d'événements étendus à l'aide de l'éditeur de requête](../Topic/Create%20an%20Extended%20Events%20Session%20Using%20Query%20Editor.md)  
  
  