---
title: Configurer SSIS sur Linux avec ssis-conf | Documents Microsoft
description: "Cet article explique comment configurer SQL Server Integration Services sur Linux avec l’utilitaire ssis-conf."
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.date: 09/26/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 46327772e8c22f76770bc51f72817ceedffae469
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="configure-sql-server-integration-services-on-linux-with-ssis-conf"></a>Configurer SQL Server Integration Services sur Linux avec ssis-conf

`ssis-conf`est un script de configuration quand vous installez SQL Server Integration Services (SSIS) pour Red Hat Enterprise Linux et Ubuntu. Vous pouvez utiliser cet utilitaire pour configurer les propriétés suivantes :

| Command |  Description |
|-------------|---------------------------------------------------------------------|
| Set-edition | Définir l’édition de SQL Server                                       |
| Données de télémétrie   | Activer ou désactiver le service de télémétrie SQL Server Integration Services |
| configurer       | Initialiser et le programme d’installation de Microsoft SQL Server Integration Services      |
|||

## <a name="how-to-run-ssis-conf"></a>Procédure d’exécution ssis-conf

Les exemples de cet article exécuter `ssis-conf` de spécifier le chemin d’accès complet : `/opt/ssis/bin/ssis-conf`. Si vous accédez à ce chemin d’accès avant d’exécuter `ssis-conf`, vous pouvez exécuter l’utilitaire dans le contexte du répertoire actif : `./ssis-conf`.

Assurez-vous que vous exécutez les commandes décrites dans cet article avec des privilèges de racine. Par exemple, exécutez `sudo /opt/ssis/bin/ssis-conf setup` et non `/opt/ssis/bin/ssis-conf setup`.

Pour exécuter ces commandes avec des messages dans la langue que vous préférez, vous pouvez spécifier des paramètres régionaux. Par exemple, pour afficher des invites en chinois, exécutez la commande suivante :

`sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="use-set-edition-to-set-the-edition-of-sql-server-integration-services"></a>Set-edition permet de définir l’édition de SQL Server Integration Services

L’édition de SSIS est alignée avec l’édition de SQL Server.

Entrez la commande suivante :

`$ sudo /opt/ssis/bin/ssis-conf set-edition`

Après avoir entré la commande, vous voyez le message suivant :

```
Choose an edition of SQL Server:

1) Evaluation (free, no production use rights, 180-day limit)

2) Developer (free, no production use rights)

3) Express (free)

4) Web (PAID)

5) Standard (PAID)

6) Enterprise (PAID)

7) Enterprise Core (PAID)

8) I bought a license through a retail sales channel and have a product key to enter.

Details about editions can be found at

https://go.microsoft.com/fwlink/?LinkId=852748&clcid=0x409

Use of PAID editions of this software requires separate licensing through a

Microsoft Volume Licensing program.

By choosing a PAID edition, you are verifying that you have the appropriate

number of licenses in place to install and run this software.

Enter your edition(1-8):
```

Si Entrez une valeur comprise entre 1 et 7, le système configure une édition gratuite ou payante. Si vous entrez 8, l’utilitaire vous invite à entrer la clé de produit que vous avez acheté :

```
Enter the 25-character product key:
```

## <a name="use-telemetry-to-configure-customer-feedback"></a>Utilisez la télémétrie pour configurer les commentaires des clients

Le `telemetry` commande détermine si SSIS envoie des commentaires à Microsoft.

Pour les éditions gratuites (autrement dit, les éditions Express, Developer et Evaluation), le service de télémétrie est toujours activé. Si vous avez une édition gratuite, vous ne pouvez pas utiliser le `telemetry` commande pour désactiver la télémétrie.

Entrez la commande suivante :

`$ sudo /opt/ssis/bin/ssis-conf telemetry`

Pour les éditions payantes, après avoir entré la commande, vous consultez le message suivant :

```
Send feature usage data to Microsoft. Feature usage data includes information
about your hardware configuration and how you use SQL Server Integration Services.

[Yes/No]:
```

Si choisissez **Oui**, le service de télémétrie est activé et commence à s’exécuter. Le service démarre automatiquement après chaque démarrage. Si choisissez **non**, le service de télémétrie s’arrête et est désactivée.

## <a name="use-setup-to-initialize-and-set-up-microsoft-sql-server-integration-services"></a>Utilisez le programme d’installation pour initialiser et configurer Microsoft SQL Server Integration Services

Utilisez la `setup` commande chaque fois que vous installez SSIS.

Entrez la commande suivante :

`sudo /opt/ssis/bin/ssis-conf setup`

L’utilitaire vous invite à accepter ou à fournir des valeurs pour les éléments suivants :
-   Licence de produit
-   CLUF
-   Service de télémétrie
-   La langue utilisée par les Services d’intégration

Pour exécuter le `setup` de commandes avec des messages dans la langue que vous préférez, vous pouvez spécifier des paramètres régionaux. Par exemple, pour afficher des invites en chinois, exécutez la commande suivante : `sudo LC_ALL=zh_CN.UTF-8 /opt/ssis/bin/ssis-conf setup`.

## <a name="ssisconf-format"></a>format de SSIS.conf

Les éléments suivants `/var/opt/ssis/ssis.conf` fichier fournit un exemple de chaque paramètre.

Pour SQL Server, vous pouvez modifier les paramètres du système en modifiant les valeurs dans le `mssql.conf` fichier. Pour SSIS, vous **ne peut pas** modifier les paramètres système en modifiant les valeurs dans le `ssis.conf` fichier. Le `ssis.conf` fichier affiche uniquement les résultats de l’installation. Si vous souhaitez modifier les paramètres de SSIS, vous pouvez supprimer la `ssis.conf` et exécutez le `setup` réexécutez la commande.

Voici un exemple `ssis.conf` fichier. Chaque champ correspond au résultat d’une étape d’installation.

```
[LICENSE]
                       
registered = Y        
                       
pid = enterprisecore  
                       
[EULA]
                       
accepteula = Y        
                       
[TELEMETRY]
                       
enabled = Y           
                       
[language]
                       
lcid = 2052
```