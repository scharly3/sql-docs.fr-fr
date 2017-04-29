---
title: "Bo&#238;te de dialogue Cr&#233;er une nouvelle condition ou Ouvrir une condition, page G&#233;n&#233;ral | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.dmf.condition.f1"
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
caps.latest.revision: 30
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 30
---
# Bo&#238;te de dialogue Cr&#233;er une nouvelle condition ou Ouvrir une condition, page G&#233;n&#233;ral
  Utilisez cette boîte de dialogue pour créer ou modifier une condition de la Gestion basée sur des stratégies. Une condition est une expression booléenne qui spécifie un jeu d'états autorisés d'une cible gérée de la Gestion basée sur des stratégies en ce qui concerne des facettes. Les propriétés qui peuvent être sélectionnées dans la zone **Expression/Champ** dépendent de la facette utilisée. Pour plus d’informations sur le rapport entre les conditions et les facettes et stratégies, consultez [Administrer des serveurs à l’aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
## Options  
 **Nom**  
 Pour une nouvelle condition, tapez le nom de la nouvelle condition. Pour une condition existante, le nom est affiché.  
  
 **Facette**  
 Facette utilisée par cette condition.  
  
 **AndOr**  
 Quand vous ajoutez plusieurs expressions, indique si les expressions doivent être jointes à l’aide de **Et** ou **Ou**. Reste vierge lorsqu'il n'y a qu'une seule expression.  
  
 **Champ**  
 Chaque facette expose une ou plusieurs propriétés qui peuvent être définies. Dans la zone de champ, sélectionnez une propriété dans la liste de propriétés disponibles afin de créer une expression pour cette condition.  
  
 **Opérateur**  
 Sélectionnez un opérateur de comparaison pour cette expression. Les opérateurs sont les suivants : =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN. Les opérateurs ne sont pas tous disponibles pour certaines propriétés.  
  
 **Valeur**  
 Paramètre de valeur pour cette expression. Les valeurs autorisées dépendent de la facette. Les valeurs peuvent être VRAI/FAUX, chaîne ou numérique. Les valeurs de chaîne doivent être placées entre guillemets simples, par exemple **'AdventureWorks'**. Les opérateurs ne sont pas tous disponibles pour certaines propriétés.  
  
## Regroupement de clauses  
 Les clauses peuvent être regroupées pour fonctionner comme une unité unique, distincte du reste de la requête, à l'instar de la mise entre parenthèses d'une expression dans une équation mathématique ou une instruction logique. Le regroupement de clauses est utile pour générer des requêtes complexes.  
  
 **Pour regrouper des clauses**  
  
-   Appuyez sur la touche MAJ ou CTRL, puis cliquez sur deux clauses (ou plus) pour sélectionner une plage. Cliquez avec le bouton droit sur la zone sélectionnée, puis cliquez sur **Regrouper des clauses**.  
  
## Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  