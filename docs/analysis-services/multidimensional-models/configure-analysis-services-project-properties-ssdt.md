---
title: Configurer les propriétés de projet Analysis Services (SSDT) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.TOOLSOPTIONSPAGES.BUSINESS_INTELLIGENCE_DESIGNERS.ANALYSIS_SERVICES_DESIGNERS.GENERAL
helpviewer_keywords:
- projects [Analysis Services], properties
ms.assetid: d9786c66-7d8c-48e3-950d-3f25044b4ce2
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1715c22cf3976a3ad888081436bb322b38451308
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="configure-analysis-services-project-properties-ssdt"></a>Configurer les propriétés d'un projet Analysis Services (SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet est défini avec certaines propriétés par défaut qui affectent la génération et déploiement de le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projet.  
  
 Pour modifier les propriétés du projet, cliquez avec le bouton droit sur l’objet de projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis sélectionnez **Propriétés**. Vous pouvez également cliquer sur **Propriétés** dans le menu Projet.  
  
## <a name="property-description"></a>Description de la propriété  
 Le tableau suivant décrit chacune des propriétés de projet, répertorie les valeurs par défaut et fournit des informations sur la modification de ces valeurs.  
  
|Propriété|Paramètre par défaut|Description|  
|--------------|---------------------|-----------------|  
|Générer / Édition du serveur de déploiement|L'édition [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée pour développer le projet|Indique l'édition du serveur sur lequel les projets seront déployés. Si vous collaborez avec plusieurs développeurs sur un projet, les développeurs doivent être familiarisés avec l'édition du serveur pour connaître les fonctionnalités à incorporer dans le projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|Générer / Édition du serveur de déploiement|La version utilisée pour développer les projets|Indique la version du serveur sur lequel les projets seront déployés.|  
|Générer / Sorties|/bin|Chemin relatif pour la sortie du processus de génération de projet|  
|Générer / Supprimer les mots de passe|True|Indique si les mots de passe connus seront supprimés des chaînes de connexion écrites dans le répertoire de sortie pendant le processus de génération. Les mots de passe sont supprimés pour renforcer la sécurité Si les mots de passe sont supprimés, vous devez les fournir lors du déploiement du projet pour permettre à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'accéder aux données sources.|  
|Débogage / Démarrer l'objet|\<Objet actif >|Indique si l'objet sera démarré lors du débogage.|  
|Déploiement / Mode de déploiement|Déployer uniquement ce qui a changé|Par défaut, seules les modifications des objets du projet sont déployées (à condition qu'aucune autre modification n'ait été apportée directement aux objets en dehors du projet). Vous pouvez également choisir de déployer tous les objets du projet à chaque déploiement. Pour optimiser les performances, utilisez l'option Déployer uniquement ce qui a changé.|  
|Déploiement / Option de traitement|Valeur par défaut|Par défaut, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] détermine le type de traitement nécessaire lorsque les modifications des objets sont déployées. Cette approche résulte en un temps de déploiement réduit. Cependant, vous pouvez également choisir d'effectuer un traitement complet ou aucun traitement à chaque déploiement.|  
|Déploiement / Déploiement transactionnel|False|Par défaut, le déploiement des objets modifiés ou de tous les objets n'est pas transactionnel avec le traitement des objets déployés. Le déploiement peut réussir et être conservé même si le traitement échoue. Vous pouvez modifier cette valeur par défaut pour incorporer le déploiement et le traitement dans une seule transaction.|  
|Déploiement / Serveur cible|localhost|Par défaut, les objets de base de données d’un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sont déployés dans l’instance par défaut d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur l’ordinateur local sur lequel vous utilisez [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] . Modifiez cette valeur par défaut pour spécifier une instance nommée sur l'ordinateur local ou n'importe quelle autre instance sur un ordinateur distant sur lequel vous avez l'autorisation de créer des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|Déploiement / Base de données|\<nom du projet >|Par défaut, le nom de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans laquelle les objets du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] seront instanciés après le déploiement est le nom du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] au moment de sa définition. Modifiez cette propriété pour modifier le nom de la base de données sur l’instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spécifiée par la propriété Server.|  
  
## <a name="property-configurations"></a>Configurations des propriétés  
 Les propriétés sont définies sur la base d'une configuration. Les configurations de projet permettent aux développeurs d'utiliser un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avec différents paramètres de génération, de débogage et de déploiement sans modifier les fichiers de projet XML sous-jacents directement.  
  
 Un projet est créé avec une seule configuration, appelée Développement. Vous pouvez créer d'autres configurations et passer de l'une à l'autre à l'aide du Gestionnaire de configuration.  
  
 Tant que d'autres configurations n'ont pas été créées, tous les développeurs utilisent cette configuration commune. Cependant, au cours des différentes phases de développement d'un projet, telles que le développement initial et le test d'un projet, les développeurs peuvent utiliser différentes sources de données et déployer le projet sur différents serveurs à des fins distinctes. Les configurations vous permettent de conserver ces différents paramètres dans différents fichiers de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer des projets Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)   
 [Déployer des projets Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
