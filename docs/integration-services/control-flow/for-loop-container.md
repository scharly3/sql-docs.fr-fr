---
title: "Conteneur de boucles For | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.forloopcontainerdetails.f1"
  - "sql13.dts.designer.forloopcontainer.f1"
helpviewer_keywords: 
  - "repeating control flow"
  - "conteneurs [Integration Services], Boucle For"
  - "conteneur de boucles For"
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
caps.latest.revision: 55
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 54
---
# Conteneur de boucles For
  Le conteneur de boucles For définit un flux de contrôle répétitif dans un package. La mise en œuvre de la boucle est similaire à la structure de bouclage **For** des langages de programmation. Dans chaque répétition de la boucle, le conteneur de boucles For évalue une expression et répète son flux de travail jusqu'à ce que l'expression retourne la valeur **False**.  
  
 Le conteneur de boucles For utilise les éléments suivants pour définir la boucle :  
  
-   Une expression d'initialisation facultative qui attribue des valeurs aux compteurs de la boucle  
  
-   Une expression d'évaluation qui permet de déterminer si la boucle doit s'arrêter ou continuer  
  
-   Une expression d'itération facultative qui incrémente ou décrémente le compteur de la boucle  
  
 Le schéma suivant illustre un conteneur de boucles For avec une tâche Envoyer un message. Si l'expression d'initialisation est `@Counter = 0`, que l'expression d'évaluation est `@Counter < 4` et que l'expression d'itération est `@Counter = @Counter + 1`, la boucle se répète quatre fois et envoie quatre messages électroniques.  
  
 ![Un conteneur de boucles For répète une tâche quatre fois.](../../integration-services/control-flow/media/ssis-forloop.gif "Un conteneur de boucles For répète une tâche quatre fois.")  
  
 Les expressions doivent être des expressions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] valides.  
  
 Pour créer les expressions d'initialisation et d'assignation, vous pouvez utiliser l'opérateur d'affectation (=). Cet opérateur n'est pas pris en charge par la grammaire d'expression Integration Services et ne peut être utilisé que par les types d'expression d'initialisation et d'assignation du conteneur de boucles For. Toute expression qui utilise l’opérateur d’affectation doit contenir la syntaxe `@Var = <expression>`, où **Var** représente une variable d’exécution et \<expression> indique une expression qui suit les règles de la syntaxe d’expression [!INCLUDE[ssIS](../../includes/ssis-md.md)]. L'expression peut comprendre les variables, les littéraux et l'ensemble des opérateurs et des fonctions pris en charge par la grammaire d'expression SSIS. L'expression doit correspondre à une valeur dont le type de données peut être converti vers le type de données de la variable.  
  
 Un conteneur de boucles For ne peut avoir qu'une seule expression d'évaluation. Par conséquent, le conteneur de boucles For exécute tous ses éléments de flux de contrôle le même nombre de fois. Étant donné que le conteneur de boucles For peut comprendre d'autres conteneurs de boucles For, vous pouvez créer des boucles imbriquées et mettre en œuvre un bouclage complexe dans les packages.  
  
 Vous pouvez configurer une propriété de transaction sur le conteneur de boucles For afin de définir une transaction pour un sous-ensemble du flux de contrôle du package. Ainsi, vous pouvez gérer les transactions de façon plus précise. Par exemple, si un conteneur de boucles For répète un flux de contrôle qui met à jour plusieurs fois les données d'une table, vous pouvez configurer la boucle For et son flux de contrôle de manière à utiliser une transaction empêchant toute mise à jour si toutes les données ne sont pas mises à jour correctement. Pour plus d’informations, consultez [Transactions Integration Services](../../integration-services/integration-services-transactions.md).  
  
## Configuration du conteneur de boucles For  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de boucle For](../Topic/For%20Loop%20Editor.md)  
  
-   [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez la documentation relative à la classe **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** dans le Guide du développeur.  
  
## Tâches associées  
 Pour plus d'informations sur la configuration d'un conteneur de boucles For, consultez les rubriques suivantes.  
  
-   [Configurer un conteneur de boucles For](../Topic/Configure%20a%20For%20Loop%20Container.md)  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Voir aussi  
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)   
 [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  