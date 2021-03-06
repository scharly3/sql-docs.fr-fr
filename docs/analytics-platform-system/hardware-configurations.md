---
title: Configurations matérielles (système de plateforme Analytique)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Le matériel de système de plateforme Analytique (APS) est conçu avec des unités évolutives afin que vous achetez le bon volume de stockage et le traitement en fonction des besoins de votre entreprise.
ms.date: 01/05/2017
ms.topic: article
ms.assetid: f95945b7-97ae-4ab9-bae5-c792a516acea
caps.latest.revision: 9
ms.openlocfilehash: d6f4b25584826d637db0a5f51ebe8ede458136c2
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="hardware-configurations"></a>Configurations matérielles
Le matériel de système de plateforme Analytique (APS) est conçu avec des unités évolutives afin que vous achetez le bon volume de stockage et le traitement en fonction des besoins de votre entreprise. L’application met à l’échelle stockage pour SQL Server Parallel données Wareouse (PDW) à partir de plusieurs téraoctets à 6 plus pétaoctets de données.  
  
## <a name="contents"></a>Sommaire  
  
-   [Configurations d’un Rack](#section1)  
  
-   [Configurations des racks](#section2)  

  
## <a name="section1"></a>Configurations d’un Rack  
Le premier rack dans l’application contient les composants requis pour exécuter PDW. La configuration du matériel minimale est un Rack et réseau ainsi qu’une unité d’échelle de Base. Ces diagrammes montrent les façons dont le premier rack du matériel peut être configuré. Vous pouvez avoir entre 2 et 9 nœuds de calcul dans le rack premier, selon le fournisseur de matériel.  
  
### <a name="first-rack-configurations---dell"></a>Tout d’abord en Rack Configurations - DELL  
La configuration minimale pour un dispositif de DELL a 3 nœuds de calcul. Vous pouvez ajouter jusqu'à 2 unités d’échelle des données sur le rack première pour un total de 9 nœuds de calcul.  
  
![Premières configurations rack de Dell](media/first-rack-configurations-dell.png "premières configurations rack de Dell")  
  
### <a name="first-rack-configurations---hpe"></a>Tout d’abord en Rack Configurations - HPE  
La configuration minimale requise pour un dispositif HPE a 2 nœuds de calcul. Vous pouvez ajouter jusqu'à 3 unités d’échelle des données sur le rack première pour un total de 8 nœuds de calcul.  
  
![HPE rack tout d’abord les configurations pour HPE](media/first-rack-configurations-hpe.png "HPE tout d’abord les configurations en rack")  
  
## <a name="section2"></a>Configurations des racks  
Pour augmenter la capacité de PDW, vous pouvez ajouter des unités d’échelle de données, ainsi que des composants de Rack & réseau supplémentaires que nécessaire pour fournir la puissance appropriée, mise en réseau et infrastructure du rack. Chaque Rack et un réseau supplémentaire requiert un hôte passif.  
  
Chaque fournisseur de matériel Spécifie le nombre d’unités d’échelle de données que vous pouvez ajouter étant donné la capacité de votre application. Nous vous recommandons d’ajouter suffisamment unités d’échelle de données pour afficher au moins une augmentation de 20 pour cent des performances. Par exemple, ajout d’une seule échelle des données unité vers un appareil qui a déjà 20 unités de l’échelle des données peut entraîner un gain de performances négligeable. Le gain n’est pas important du coût et des efforts.  
  
### <a name="scale-out-example---hpe"></a>Montée en puissance parallèle exemple - HPE  
Ce diagramme illustre un dispositif de 3 rack HP qui contient 20 nœuds de calcul.  
  
![Équipement HPE avec 20 nœuds de calcul](media/scale-out-hpe.png "appliance HPE avec 20 nœuds de calcul")  
  
### <a name="scale-out-example--dell-quanta"></a>Montée en puissance parallèle exemple – DELL, Quanta  
Ce diagramme illustre un dispositif de DELL ou Quanta 3 rack qui contient les nœuds de calcul 21.  
  
![Dispositif de Dell avec les nœuds de calcul 21](media/scale-out-dell.png "appliance Dell avec 21 nœuds de calcul")  
 
