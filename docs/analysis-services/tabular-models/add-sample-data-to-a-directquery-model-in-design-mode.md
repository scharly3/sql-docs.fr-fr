---
title: "Ajoutez des exemples de données à un modèle DirectQuery en Mode Création | Documents Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af1e823-85aa-4319-a93f-98b35f7c7322
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 068366df63bbe37d658345c1157a9d02eb7e5187
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="add-sample-data-to-a-directquery-model-in-design-mode"></a>Ajouter des exemples de données à un modèle DirectQuery en mode Création
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
En mode DirectQuery, les partitions de table permettent de créer des exemples de sous-ensembles de données utilisés pendant la conception du modèle ou pour créer des solutions de remplacement d’une vue complète des données.
 
 Quand vous déployez un modèle tabulaire DirectQuery, une seule partition est autorisée par table, et cette partition doit obligatoirement contenir la vue complète des données. Toute partition supplémentaire contient soit un substitue de la vue complète des données, soit un exemple de données. Dans cette rubrique, nous allons décrire la création d’un exemple de partition, avec un sous-ensemble de données.
 
 Par défaut, quand vous concevez un modèle tabulaire en mode DirectQuery dans SSDT, la base de données effective du modèle ne contient pas de données. Il existe une partition par défaut pour chaque table, et cette partition dirige toutes les requêtes vers la source de données. 
  
Vous pouvez toutefois ajouter une plus petite quantité de données d’exemple dans la base de données effective de votre modèle pour une utilisation au moment de la conception. Les exemples de données sont spécifiés à l’aide d’une requête sur un exemple de partition utilisé uniquement lors de la conception. Ils sont mis en cache en mémoire avec le modèle. Cela vous permet de valider les décisions de modélisation à mesure que vous progressez sans que cela ait d’incidence sur la source de données. Vous pouvez tester vos décisions de modélisation avec l’exemple de dataset lors de l’utilisation de l’option **Analyser dans Excel** de SQL Server Data Tools (SSDT), ou à partir d’autres applications clientes qui se connectent à la base de données de votre espace de travail.  
  
> [!TIP]  
>  Vous pouvez toujours afficher un petit ensemble de lignes intégré pour chaque table, même en mode DirectQuery sur un modèle vide Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur **Table** > **Propriétés de la table** pour afficher le dataset de 50 lignes.  
  
## <a name="create-a-sample-partition"></a>Créer un exemple de partition
 Ces instructions sont pour les modèles tabulaires créé ou mis à niveau vers le niveau de compatibilité 1200 ou supérieur. Les modèles ayant des niveaux de compatibilité inférieurs utilisent des propriétés différentes pour obtenir des données mises en cache. Pour obtenir une description des propriété, consultez [Activer le mode DirectQuery dans SSMS](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md) .  
  
1.  Dans SQL Server Data Tools, dans le diagramme ou la vue de données, cliquez sur une table de faits pour ouvrir sa page de propriétés. Les tables de faits fournissent les mesures et les données numériques agrégées de votre modèle. Vous pouvez en avoir plusieurs.  
  
2.  Cliquez sur **Table** > **Propriétés** pour ouvrir la boîte de dialogue Gestion des partitions.  
  
    Notez la partition par défaut est **(requête directe) \<nom de table >**. Il s’agit de la vue complète des données. Ne supprimez pas cette partition. Cette partition sera utilisée lors du déploiement du modèle.  
  
4.  Sélectionnez la partition, puis cliquez sur **Copier**.  

    Cela crée une copie de la partition par défaut. Toutefois, cette copie contiendra les exemples de données que vous spécifiez dans une requête. Par exemple :
  
     ![ssas_tabularproject_copypartition](../../analysis-services/tabular-models/media/ssas-tabularproject-copypartition.jpg "ssas_tabularproject_copypartition")  
  
5.  Sélectionnez la partition copiée, puis cliquez sur le bouton **Éditeur de requête SQL** pour ajouter un filtre. Réduisez la taille de vos données d’exemple lors de la création de votre modèle. Par exemple, si vous avez sélectionné **FactInternetSales** dans AdventureWorksDW, votre filtre ressemble peut-être semblable à ce qui suit :  
  
    ```  
    SELECT [dbo].[FactInternetSales].* FROM [dbo].[FactInternetSales]  
    JOIN DimSalesTerritory as ST  
    ON ST.SalesTerritoryKey = FactInternetSales.SalesTerritoryKey  
    WHERE ST.SalesTerritoryGroup='North America';  
    ```  
  
6.  Cliquez sur **Valider** pour rechercher les erreurs de syntaxe.  
  
     Notez qu’en mode DirectQuery, en plus des boutons **Nouveau** , **Copier**et **Supprimer** de la boîte de dialogue Partitions, il existe un bouton bascule qui indique soit **Définir comme exemple** , soit **Définir comme DirectQuery**.  
  
     Une seule partition peut être définie comme partition DirectQuery. Pour ce faire, sélectionnez une partition définie pour la table, puis cliquez sur **Définir comme exemple**.  
  
7.  Traitez la table.  
  


  
  
