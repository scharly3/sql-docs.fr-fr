---
title: Tuningoptions, élément (DTA) | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f82d39a90f515d4f70d9e48bef7f20996ba60f78
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="tuningoptions-element-dta"></a>TuningOptions, élément (Assistant Paramétrage de base de données)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Contient les options de paramétrage pour une session de paramétrage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|**Type de données et longueur**|Aucun.|  
|**Valeur par défaut**|Aucun.|  
|**Occurrence**|Ce paramètre est facultatif. Si cet élément est utilisé, il ne peut être utilisé qu'une seule fois pour l'élément **DTAInput** .|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Éléments|  
|------------------|--------------|  
|**Élément parent**|[DTAInput, élément &#40; DTA &#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Éléments enfants**|Élément**ReportSet** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**TuningLogTable** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**NumberOfEvents** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [Tuningtimeinmin, élément &#40; DTA &#41;](../../tools/dta/tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB, élément &#40;DTA&#41;](../../tools/dta/storageboundinmb-element-dta.md)<br /><br /> Élément**MaxKeyColumnsInIndex** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**MaxColumnsInIndex** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**MinPercentageImprovement** . Pour plus d'informations, consultez le [schéma XML de l'Assistant Paramétrage du moteur de base de données](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TESTSERVER, élément &#40; DTA &#41;](../../tools/dta/testserver-element-dta.md)<br /><br /> [Featureset, élément &#40; DTA &#41;](../../tools/dta/featureset-element-dta.md)<br /><br /> [Partitioning, élément &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)<br /><br /> [Droponlymode, élément &#40; DTA &#41;](../../tools/dta/droponlymode-element-dta.md)<br /><br /> [Keepexisting, élément &#40; DTA &#41;](../../tools/dta/keepexisting-element-dta.md)<br /><br /> [Onlineindexoperation, élément &#40; DTA &#41;](../../tools/dta/onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect, élément &#40;DTA&#41;](../../tools/dta/databasetoconnect-element-dta.md)<br /><br /> Élément**IgnoreConstantsInWorkload** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> Élément**RetainShellDB** . Pour plus d'informations, consultez l'article [Database Engine Tuning Advisor XML schema](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Exemple  
 Pour obtenir des exemples de l’élément **TuningOptions**, consultez les [exemples de fichiers d’entrée XML &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fichiers d’entrée XML &#40;Assistant Paramétrage du moteur de base de données&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
