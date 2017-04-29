---
title: "S&#39;abonner &#224; des publications | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.conc.subtopubs.f1"
helpviewer_keywords: 
  - "abonnements [réplication SQL Server], à propos des abonnements"
  - "abonnements par extraction de données (pull) [réplication SQL Server]"
  - "abonnements [SQL Server replication]"
  - "abonnements par émission de données (push) [réplication SQL Server], à propos des abonnements par émission de données"
  - "abonnement aux réplications de fusion [réplication SQL Server]"
  - "abonnement aux réplications de fusion [réplication SQL Server], à propos de l’abonnement"
  - "publications [réplication SQL Server], abonnement"
  - "abonnements par envoi de données (push) [SQL Server replication]"
  - "abonnements par extraction (pull) [réplication SQL Server], à propos des abonnements par extraction"
  - "réplication d'instantané [SQL Server], abonnement"
  - "réplication transactionnelle, abonnement"
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# S&#39;abonner &#224; des publications
  Un abonnement est une demande de copie de données et d'objets de base de données d'une publication. Il définit la publication qui sera reçue, où et quand elle sera reçue. Lorsque vous planifiez des abonnements, pensez à l'endroit où vous voulez qu'ait lieu le traitement de l'agent. Le type d'abonnement choisi détermine l'emplacement d'exécution de l'agent. Avec un abonnement par envoi de données (push), l'Agent de fusion ou l'Agent de distribution s'exécute sur le serveur de distribution tandis qu'avec un abonnement par extraction de données (pull), les agents s'exécutent sur les Abonnés. Il n'est plus possible de modifier le type d'un abonnement une fois celui-ci créé.  
  
|Abonnement|Caractéristiques|Cas d'utilisation|  
|------------------|---------------------|--------------|  
|Abonnement envoyé|Avec un abonnement par envoi de données, le serveur de publication propage les modifications à un Abonné sans que ce dernier en ait fait la demande. Les modifications peuvent être envoyées à des Abonnés à la demande, en continu ou selon un horaire planifié. L'Agent de distribution ou l'Agent de fusion s'exécute sur le serveur de distribution.|Les données sont censées être synchronisées de façon permanente ou à intervalles fréquents et périodiques.<br /><br /> La publication nécessite un transfert en temps réel (ou presque) des données.<br /><br /> L'augmentation de la charge imposée au processeur d'un serveur de distribution n'affecte pas les performances.<br /><br /> Le plus souvent utilisé avec la réplication d'instantané et la réplication transactionnelle.|  
|Abonnement extrait|Dans le cas d'un abonnement par extraction, l'Abonné demande à recevoir les modifications apportées sur le serveur de publication. Ce type d'abonnement permet à l'utilisateur sur l'Abonné de déterminer le moment où les modifications sont synchronisées. L'Agent de distribution ou l'Agent de fusion s'exécute sur l'Abonné.|Avec ce type d'abonnement, les données sont en général synchronisées à la demande ou selon un horaire planifié plutôt qu'en continu.<br /><br /> La publication compte un grand nombre d'Abonnés et l'exécution de tous les agents sur un seul site ou sur le serveur de distribution entraînerait une consommation excessive des ressources.<br /><br /> Les abonnés sont autonomes, non connectés et/ou mobiles. Ils déterminent à quel moment ils se connectent et synchronisent les modifications.<br /><br /> Le plus souvent utilisé avec la réplication de fusion.|  
  
## Types d'abonnements de réplication de fusion  
 Tous les types de réplication permettent des abonnements par envoi ou extraction de données. La réplication de fusion fait la distinction entre deux types d'abonnement : les abonnements client et les abonnements serveur. Ces deux types d'abonnement sont utilisables avec les abonnements par envoi ou extraction de données. Les abonnements client sont adaptés à la plupart des Abonnés, tandis que les abonnements serveur sont généralement utilisés pour les Abonnés qui republient des données vers d'autres Abonnés. Le choix de l'abonnement a également une incidence sur la résolution des conflits.  
  
## Abonnés non-SQL Server  
 Oracle et IBM DB2 peuvent s'abonner à des publications transactionnelles et des publications d'instantané à l'aide des abonnements par envoi de données. Pour plus d’informations, consultez la page [les abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
## Création d'abonnements  
 Pour créer un abonnement, fournissez les informations suivantes :  
  
-   Nom de la publication.  
  
-   le nom de l'Abonné et de la base de données d'abonnement ;  
  
-   si l'Agent de distribution ou l'Agent de fusion s'exécute sur le serveur de distribution ou sur l'Abonné ;  
  
-   si l'Agent de distribution ou l'Agent de fusion s'exécute en continu, selon un horaire planifié ou à la demande seulement ;  
  
-   si l'Agent d'instantané doit créer un instantané initial pour l'abonnement et si l'Agent de distribution ou l'Agent de fusion doit appliquer cet instantané sur l'abonné ;  
  
-   les comptes sous lesquels l'Agent de distribution ou l'Agent de fusion s'exécute ;  
  
-   Pour la réplication de fusion, le type d'abonnement : serveur ou client.  
  
 **Pour créer un abonnement envoyé**  
  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
  
 **Pour afficher ou modifier les propriétés d'un abonnement par envoi de données**  
  
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)  
  
 **Pour supprimer un abonnement par envoi de données**  
  
 [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)  
  
> [!NOTE]  
>  La suppression d'un abonnement n'entraîne pas la suppression des objets publiés sur l'Abonné.  
  
 **Pour créer un abonnement par extraction de données**  
  
 [! INCLURE [ssManStudioFull] (.. / Token/ssManStudioFull_md.md)]: [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
  
 **Pour afficher ou modifier les propriétés d'un abonnement extrait**  
  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)  
  
 **Pour supprimer un abonnement extrait**  
  
 [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)  
  
## Voir aussi  
 [Sécuriser l'abonné](../../relational-databases/replication/security/secure-the-subscriber.md)   
 [Expiration et désactivation des abonnements](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  