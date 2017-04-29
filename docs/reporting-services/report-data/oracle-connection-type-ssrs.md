---
title: "Type de connexion Oracle (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "01/11/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
caps.latest.revision: 10
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 8
---
# Type de connexion Oracle (SSRS)
  Pour utiliser des données d'une base de données Oracle dans votre rapport, vous devez avoir un dataset basé sur une source de données de rapport de type Oracle. Ce type de source de données intégré est basé sur le fournisseur managé .NET Framework pour Oracle et requiert un composant logiciel client Oracle.  
  
 Utilisez les informations de cette rubrique pour générer une source de données. Pour obtenir des instructions détaillées, consultez [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Chaîne de connexion  
 Contactez l'administrateur de votre base de données pour connaître les informations de connexion et d'identification à utiliser pour se connecter à la source de données. L'exemple de chaîne de connexion suivant spécifie une base de données Oracle sur le serveur nommé Oracle9 utilisant Unicode. Le nom du serveur doit correspondre à ce qui est défini dans le fichier de configuration Tnsnames.ora comme nom d'instance de serveur Oracle.  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 Pour plus d’informations sur les exemples de chaînes de connexion, consultez [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md).  
  
##  <a name="Credentials"></a> Informations d'identification  
 Les informations d'identification sont obligatoires pour exécuter des requêtes, afficher l'aperçu du rapport localement et afficher l'aperçu du rapport à partir du serveur de rapports.  
  
 Après avoir publié votre rapport, vous pouvez devoir modifier les informations d'identification pour la source de données afin que les autorisations soient valides pour récupérer les données lorsque le rapport s'exécute sur le serveur de rapports.  
  
 Pour plus d’informations, consultez [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) ou [Spécifier des informations d’identification dans le Générateur de rapports](../Topic/Specify%20Credentials%20in%20Report%20Builder.md).  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Retour au début](#BackToTop)  
  
##  <a name="Query"></a> Requêtes  
 Pour créer un dataset, vous pouvez soit sélectionner une procédure stockée dans une liste déroulante, soit créer une requête SQL. Pour générer une requête, vous devez utiliser le concepteur de requêtes textuel. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes textuel &#40;Générateur de rapports&#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Vous pouvez spécifier des procédures stockées qui ne retournent qu'un seul jeu de résultats. L'utilisation des requêtes basées sur curseur n'est pas prise en charge.  
  
##  <a name="Parameters"></a> Paramètres  
 Si la requête inclut des variables de requête, les paramètres de rapport sont générés automatiquement. Les paramètres nommés sont pris en charge par cette extension. Pour Oracle version 9 ou une version ultérieure, les paramètres à valeurs multiples sont pris en charge.  
  
 Les paramètres de rapport sont créés avec des valeurs de propriétés par défaut que vous devrez peut-être modifier. Par exemple, chaque paramètre de rapport a le type de données **Texte**. Après avoir créé les paramètres de rapport, vous devrez peut-être modifier les valeurs par défaut. Pour plus d’informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Retour au début](#BackToTop)  
  
##  <a name="Remarks"></a> Notes  
 Avant de pouvoir connecter une source de données Oracle, l'administrateur système doit installer au préalable la version du fournisseur de données .NET pour Oracle qui prend en charge la récupération des données à partir de la base de données Oracle. Ce fournisseur de données doit être installé sur le même ordinateur que le Générateur de rapports, ainsi que sur le serveur de rapports.  
  
 Pour plus d'informations, consultez les documents suivants :  
  
-   [Utilisation du fournisseur de données .NET Framework pour Oracle](http://go.microsoft.com/fwlink/?LinkId=112314) sur msdn.microsoft.com  
  
-   [How to use Reporting Services to configure and to access an Oracle data source (en anglais)](http://support.microsoft.com/kb/834305)  
  
-   [Comment ajouter des autorisations pour le principal de sécurité SERVICE RÉSEAU](http://support.microsoft.com/kb/870668)  
  
###### Autres extensions de données  
 Vous pouvez également récupérer des données à partir d'une base de données Oracle à l'aide d'un type de source de données OLE DB. Pour plus d’informations, consultez [Type de connexion OLE DB &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  
  
###### Modèles de rapport  
 Vous pouvez également créer des modèles basés sur une base de données Oracle.  
  
###### Informations sur les plateformes et les versions  
 Pour plus d’informations sur la prise en charge des plateformes et des versions, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) dans la section [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la [documentation en ligne](http://go.microsoft.com/fwlink/?linkid=121312) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Retour au début](#BackToTop)  
  
##  <a name="HowTo"></a> Rubriques de procédures  
 Cette section contient des instructions pas à pas sur l'utilisation des connexions de données, des sources de données et des datasets.  
  
 [Ajouter et vérifier une connexion de données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Ajouter un filtre à un dataset &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Retour au début](#BackToTop)  
  
##  <a name="Related"></a> Sections connexes  
 Ces sections de la documentation fournissent des informations de fond d'ordre conceptuel sur les données de rapport, ainsi que des informations sur les procédures de définition, de personnalisation et d'utilisation des parties d'un rapport qui sont liées aux données.  
  
 [Datasets de rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Fournit une vue d'ensemble de l'accès aux données pour votre rapport.  
  
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
 Fournit des informations sur les connexions de données et les sources de données.  
  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Fournit des informations sur les datasets incorporés et partagés.  
  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Fournit des informations sur la collection de champs de dataset générée par la requête.  
  
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) dans la section [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la [documentation en ligne](http://go.microsoft.com/fwlink/?linkid=121312) de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Fournit des informations détaillées sur la prise en charge des plateformes et des versions pour chaque extension de données.  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [Retour au début](#BackToTop)  
  
## Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  