---
title: "STArea (type de données geography) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2082c36f483e1ebe6d532abb6d3335db127b21b1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="starea-geography-data-type"></a>STArea (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne la surface d’exposition totale d’une instance **geography**. Les résultats de STArea() sont retournés dans le carré de l’unité de mesure utilisée par l’identificateur de référence spatiale de l’instance **geography**. Par exemple, si le SRID de l’instance est 4326, STArea() retourne les résultats en mètres carrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **float**  
  
 Type de retour CLR : **SqlDouble**  
  
## <a name="remarks"></a>Notes   
 STArea() retourne 0 si une instance **geography** contient uniquement des figures à 0 et 1 dimension, ou si elle est vide.  
  
> [!NOTE]  
>  Les méthodes du type de données **geography** qui produisent une valeur de retour métrique ont des résultats distincts selon le SRID de l’instance utilisée dans la méthode. Pour plus d’informations sur les SRID, consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant utilise `STArea()` pour créer une instance `Polygon``geography` et calcule la surface du polygone.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
