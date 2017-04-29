---
title: "Le&#231;on 6 : Utilisation des param&#232;tres avec le mod&#232;le de d&#233;ploiement de projet dans SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Le&#231;on 6 : Utilisation des param&#232;tres avec le mod&#232;le de d&#233;ploiement de projet dans SSIS
SQL Server 2012 introduit un nouveau modèle de déploiement qui permet de déployer vos projets sur le serveur Integration Services. Le serveur Integration Services vous permet de gérer et d'exécuter les packages, et de configurer leurs valeurs d'exécution.  
  
Dans cette leçon, vous allez modifier le package que vous avez créé dans [Leçon 5 : Ajouter des configurations de package SSIS pour le modèle de déploiement de package](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) pour utiliser le modèle de déploiement de package. Vous remplacerez la valeur de configuration par un paramètre pour spécifier l'emplacement des exemples de données. Vous pouvez également copier le package final de la leçon 5 inclus dans le didacticiel.  
  
À l'aide de l'Assistant Configuration de projet Integration Services, vous convertirez le projet en modèle de déploiement de projet, et vous utiliserez un paramètre au lieu d'une valeur de configuration pour définir la propriété Directory. Cette leçon couvre partiellement les étapes que vous suivriez pour convertir les packages SSIS existants en nouveau modèle de déploiement de projet.  
  
Quand vous réexécutez le package, le service Integration Services utilise le paramètre pour donner sa valeur à la variable, qui à son tour met à jour la propriété Répertoire. Ainsi, le package itère dans les fichiers du nouveau dossier de données spécifié par la valeur du paramètre, et non du dossier défini dans le fichier de configuration du package.  
  
> [!IMPORTANT]  
> Pour suivre ce didacticiel, vous devez disposer de l'exemple de base de données **AdventureWorksDW2012** . Pour plus d’informations sur l’installation et le déploiement de **AdventureWorksDW2012**, consultez [Considérations relatives à l’installation d’exemples de bases de données et d’exemples de code SQL Server](http://technet.microsoft.com/en-us/library/ms161556%28v=sql.105%29).  
  
## Tâches de la leçon  
Cette leçon contient les tâches suivantes :  
  
1.  [Étape 1 : copie du package de la leçon 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  
2.  [Étape 2 : Conversion du projet en modèle de déploiement de projet](../integration-services/step-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Étape 3 : Test du package de la leçon 6](../integration-services/step-3-testing-the-lesson-6-package.md)  
  
4.  [Étape 4 : Déploiement du package de la leçon 6](../integration-services/step-4-deploying-the-lesson-6-package.md)  
  
## Démarrer la leçon  
[Étape 1 : copie du package de la leçon 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  