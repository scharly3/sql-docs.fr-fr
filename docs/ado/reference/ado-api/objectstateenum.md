---
title: ObjectStateEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cf7bdb66b8c8de0e45417e85005d7eda90fdc014
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="objectstateenum"></a>ObjectStateEnum
Spécifie si un objet est ouvert ou fermé, la connexion à une source de données, l’exécution d’une commande ou la récupération des données.  
  
|Constante|Valeur| Description|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|Indique que l’objet est fermé.|  
|**adStateOpen**|1|Indique que l’objet est ouvert.|  
|**adStateConnecting**|2|Indique que l’objet se connecte.|  
|**adStateExecuting**|4|Indique que l’objet s’exécute une commande.|  
|**adStateFetching**|8|Indique que les lignes de l’objet sont récupérés.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC équivalent  
 Package : **com.ms.wfc.data**  
  
|Constante|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[State, propriété (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
