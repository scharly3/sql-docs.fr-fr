---
title: "Le&#231;on&#160;1&#160;: publication de donn&#233;es &#224; l&#39;aide de la r&#233;plication transactionnelle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "réplication [SQL Server], didacticiels"
ms.assetid: 9c55aa3c-4664-41fc-943f-e817c31aad5e
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Le&#231;on&#160;1&#160;: publication de donn&#233;es &#224; l&#39;aide de la r&#233;plication transactionnelle
Dans cette leçon, vous créez une publication transactionnelle en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour publier un sous-ensemble filtré de la table **Product** de l’exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Vous allez aussi ajouter à la liste d'accès à la publication le compte de connexion SQL Server utilisée par l'Agent de distribution. Avant de commencer ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur à la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
### Pour créer une publication et définir des articles  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication**, cliquez avec le bouton droit sur le dossier **Publications locales**, puis cliquez sur **Nouvelle publication**.  
  
    L'Assistant Configuration de la publication démarre.  
  
3.  Dans la page Base de données de publication, sélectionnez [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis cliquez sur **Suivant**.  
  
4.  Dans la page Type de publication, sélectionnez **Publication transactionnelle**, puis cliquez sur **Suivant**.  
  
5.  Dans la page Articles, développez le nœud **Tables**, cochez la case **Product**, puis développez **Product** et décochez les cases **ListPrice** et **StandardCost**. Cliquez sur **Suivant**.  
  
6.  Dans la page Filtrer les lignes de la table, cliquez sur **Ajouter**.  
  
7.  Dans la boîte de dialogue **Ajouter un filtre**, cliquez sur la colonne **SafetyStockLevel**, cliquez sur la flèche droite pour ajouter la colonne à la clause WHERE de la requête de filtre et modifiez la clause WHERE comme suit :  
  
    ```  
    WHERE [SafetyStockLevel] < 500  
    ```  
  
8.  Cliquez sur **OK**, puis sur **Suivant**.  
  
9. Cochez la case **Créer un instantané immédiatement et garder ce dernier disponible pour l’initialisation des abonnements** et cliquez sur **Suivant**.  
  
10. Dans la page Sécurité de l’agent, décochez la case **Utiliser les paramètres de sécurité de l’Agent d’instantané**.  
  
11. Cliquez sur **Paramètres de sécurité** pour l’Agent d’instantané, entrez \<*nom_ordinateur>***\repl_snapshot** dans la zone **Compte de processus**, spécifiez le mot de passe du compte et cliquez sur **OK**.  
  
12. Répétez l’étape précédente pour définir repl_logreader comme compte de processus de l’Agent de lecture du journal, puis cliquez sur **Terminer**.  
  
13. Dans la page Terminer l’Assistant, entrez **AdvWorksProductTrans** dans la zone **Nom de la publication**, puis cliquez sur **Terminer**.  
  
14. Une fois la publication créée, cliquez sur **Fermer** pour terminer l’Assistant.  
  
### Pour afficher l'état d'une génération d'instantané  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis développez le dossier **Réplication**.  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis cliquez sur **Afficher l’état de l’Agent d’instantané**.  
  
3.  L'état en cours du travail de l'Agent d'instantané pour la publication s'affiche. Vérifiez que le travail d'instantané a bien réussi avant de passer à la leçon suivante.  
  
### Pour ajouter la connexion de l'Agent de distribution à la liste d'accès à la publication  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, puis développez le dossier **Réplication**.  
  
2.  Dans le dossier **Publications locales**, cliquez avec le bouton droit sur **AdvWorksProductTrans**, puis cliquez sur **Propriétés**.  
  
    La boîte de dialogue **Propriétés de la publication** s’affiche.  
  
3.  Sélectionnez la page **Liste d’accès à la publication**, puis cliquez sur **Ajouter**.  
  
4.  \Dans la boîte de dialogue **Ajouter un accès à une publication**, sélectionnez *nom_ordinateur>***\repl_distribution** et cliquez sur **OK**. Cliquez sur **OK**.  
  
## Étapes suivantes  
Vous avez créé avec succès la publication transactionnelle. Ensuite, vous allez créer l'abonnement à cette publication. Consultez [Leçon 2 : Création d’un abonnement à la publication transactionnelle](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
## Voir aussi  
[Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md)  
[Define an Article](../../relational-databases/replication/publish/define-an-article.md)  
[Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-snapshot.md)  
  
  
  