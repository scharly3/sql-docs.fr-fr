---
title: "Le&#231;on 2&#160;: Sp&#233;cification des informations de connexion (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "05/23/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 53
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 51
---
# Le&#231;on 2&#160;: Sp&#233;cification des informations de connexion (Reporting Services)
Après avoir ajouté un rapport au projet Didacticiel, vous devez définir une *source de données*, qui sont des informations de connexion que le rapport utilise pour accéder aux données à partir d’une base de données relationnelle, d’une base de données multidimensionnelle ou d’une autre ressource.  
  
Dans cette leçon, vous allez utiliser l’exemple de base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] comme source de données. Ce didacticiel part du principe que cette base de données se trouve dans une instance par défaut du [!INCLUDE[ssDE](../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installée sur l’ordinateur local.  
  
### Pour configurer une connexion  
  
1.  Dans le volet **Données du rapport**, cliquez sur **Nouveau**, puis sur **Source de données**.  
Si le volet **Données du rapport** n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  
  
   2.  Dans le champ **Nom**, tapez *Adventureworks2014*.  
  
3.  Vérifiez que l’option **Connexion incorporée** est sélectionnée.  
  
4.  Dans **Type**, sélectionnez **Microsoft SQL Server**.  
  
5.  Dans **Chaîne de connexion**, tapez ce qui suit :  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
Cette chaîne de connexion part du principe que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], le serveur de rapports et la base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] sont tous installés sur l’ordinateur local et que vous êtes autorisé à ouvrir une session sur la base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. Si votre base de données AdventureWorks2014 n’est pas sur l’ordinateur local, modifiez la chaîne de connexion et remplacez *localhost* par le nom de votre instance de serveur de base de données.
   
  
 > [!NOTE]  
 > Si vous utilisez [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services ou une instance nommée, la chaîne de connexion doit comporter des informations sur l'instance :  
 >   
 > `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
 >   
 > Pour plus d’informations sur les chaînes de connexion, consultez :  
 > *  [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
    > * [Boîte de dialogue Propriétés de la source de données, Général](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
        
  
6.  Cliquez sur **Informations d’identification** dans le volet gauche, puis sur **Utiliser l’authentification Windows (sécurité intégrée)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] La source de données [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] est ajoutée au volet **Données du rapport**.  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## Tâche suivante  
Vous avez défini avec succès une connexion à l’exemple de base de données [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)]. Vous allez ensuite créer un rapport. Voir [Leçon 3 : Définition d’un dataset destiné à un rapport de table &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## Voir aussi  
[Boîte de dialogue Propriétés de la source de données, Général](../Topic/Data%20Source%20Properties%20Dialog%20Box,%20General.md)  
[Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  