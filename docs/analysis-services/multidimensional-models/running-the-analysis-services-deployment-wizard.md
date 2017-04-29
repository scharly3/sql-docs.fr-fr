---
title: "Ex&#233;cution de l&#39;Assistant D&#233;ploiement d&#39;Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistant Déploiement d’Analysis Services, exécution"
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: 41
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 38
---
# Ex&#233;cution de l&#39;Assistant D&#233;ploiement d&#39;Analysis Services
  Lorsque vous utilisez l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour déployer un projet [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vous pouvez exécuter l'Assistant de plusieurs manières :  
  
-   **Interactivement** Lorsque vous exécutez l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de manière interactive, il génère un script de déploiement XML basé sur les fichiers d'entrée, modifié de manière interactive par l'entrée utilisateur. L'Assistant applique les modifications utilisateur uniquement au script de déploiement. Il ne modifie pas les fichiers d'entrée. Pour plus d’informations sur les fichiers d’entrée, voir [Précisions sur les fichiers d’entrée utilisés pour créer le script de déploiement](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md).  
  
-   **À partir de l’invite de commandes** Lorsque vous exécutez l’Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de l’invite de commandes, il génère un script de déploiement \(XMAL\) (XML for Analysis) basé sur les commutateurs que vous utilisez pour l’exécuter. L'Assistant peut effectuer les opérations suivantes : vous demander une entrée utilisateur et modifier les fichiers d'entrée en fonction de cette entrée, exécuter un déploiement automatisé en mode silencieux en utilisant les fichiers d'entrée tels quels, ou créer un script de déploiement que vous pouvez utiliser ultérieurement.  
  
## Exécution de l'Assistant Déploiement d'Analysis Services de manière interactive  
 Lorsque vous exécutez l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de manière interactive, il lit les valeurs des fichiers d'entrée et affiche ces informations. Vous pouvez modifier ces valeurs d'entrée, telle que la destination du déploiement, les paramètres de configuration, les options de déploiement et les mots de passe des chaînes de connexion, ou les laisser telles quelles. Si vous changez les valeurs d'entrée, l'Assistant utilise ces modifications lors de la génération du script de déploiement XMLA. Toutefois, il ne modifie pas les valeurs du fichier d'entrée.  
  
> [!NOTE]  
>  Pour que l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] modifie les valeurs d'entrée, exécutez-le à partir de l'invite de commandes et configurez-le pour fonctionner en mode de fichier de réponses.  
  
 Après avoir vérifié les valeurs d'entrée et effectué les modifications appropriées, l'Assistant génère le script de déploiement XMLA. Vous pouvez exécuter ce script de déploiement immédiatement sur le serveur de destination ou l'enregistrer en vue d'une utilisation ultérieure.  
  
#### Pour exécuter l'Assistant Déploiement d'Analysis Services de manière interactive  
  
-   Dans le menu **Démarrer**, pointez successivement sur **Tous les programmes**, **Microsoft SQL Server**et **Analysis Services**, puis cliquez sur **Assistant Déploiement**.  
  
     —ou—  
  
-   Dans le dossier **Projets** du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], double\-cliquez sur le fichier *\<nom_projet\>*.asdatabase.  
  
    > [!NOTE]  
    >  Si vous ne trouvez pas le fichier *\<nom_projet\>*.asdatabase, essayez d’utiliser la fonction de recherche en spécifiant \*.asdatabase.  
  
## Exécution de l'Assistant Déploiement d'Analysis Services à partir de l'invite de commandes  
 Vous pouvez également exécuter l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de l'invite de commandes. Lorsque vous exécutez l'Assistant à l'invite de commandes, vous fournissez le chemin d'accès complet au fichier .asdatabase et exécutez l'Assistant en l'un des modes suivants :  
  
 **Mode de fichier de réponses**  
 Dans ce mode, l’Assistant permet de modifier de manière interactive les fichiers d’entrée générés à l’origine lors de la création du projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. L'Assistant enregistre les fichiers d'entrée modifiés avant de générer le script de déploiement XMLA. Les fichiers d'entrée deviennent le nouveau point de départ de la prochaine exécution de l'Assistant.  
  
 Pour exécuter l’Assistant en mode de fichier de réponses, utilisez le commutateur **\/a**.  
  
 **Mode silencieux**  
 En mode silencieux, l'Assistant exécute un déploiement automatisé en fonction des informations qui se trouvent dans les fichiers d'entrée.  
  
 Pour exécuter l’Assistant en mode silencieux, utilisez le commutateur **\/s**. Lorsque vous exécutez l'Assistant en mode silencieux, les messages sont affichés sur la console ou enregistrés dans un fichier journal (s'il en existe un).  
  
 **Mode de sortie**  
 En mode de sortie, l'Assistant génère un script de déploiement XMLA pour l'exécuter plus tard en fonction des fichiers d'entrée.  
  
 Pour exécuter l’Assistant en mode de sortie, utilisez le commutateur **\/o** et fournissez un nom de fichier de sortie.  
  
 Pour plus d’informations sur les commutateurs de ligne de commande, voir [Déployer des solutions de modèle avec l’utilitaire de déploiement](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md).  
  
 La procédure suivante explique comment exécuter l'Assistant Déploiement [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir de l'invite de commandes.  
  
#### Pour exécuter l'Assistant Déploiement d'Analysis Services à partir de l'invite de commandes  
  
1.  Ouvrez une invite de commandes, puis accédez au dossier C:\\Program Files \(x86\)\\Microsoft SQL Server\\120\\Tools\\Binn\\ManagementStudio  
  
2.  Tapez **Microsoft.AnalysisServices.Deployment.exe** , suivi des commutateurs qui correspondent au mode dans lequel vous souhaitez exécuter l'Assistant.  
  
## Voir aussi  
 [Description du script de déploiement Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Deploy Model Solutions Using the Deployment Wizard](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  