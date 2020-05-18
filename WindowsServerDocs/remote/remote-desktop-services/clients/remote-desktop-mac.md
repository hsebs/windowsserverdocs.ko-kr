---
title: Bien démarrer avec le client macOS
description: Découvrez comment configurer le client Bureau à distance pour Mac
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 7afc65f8-3158-49c9-9d48-4dab1c69afba
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 05/06/2020
ms.localizationpriority: medium
ms.openlocfilehash: 6c219a6dbc5922e9d7240b3004c1dd92eb7d057a
ms.sourcegitcommit: 67116322915066b85decb4261d47cedec2cfe12f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82903460"
---
# <a name="get-started-with-the-macos-client"></a>Bien démarrer avec le client macOS

>S'applique à : Windows 10, Windows 8.1, Windows Server 2012 R2, Windows Server 2016

Le client Bureau à distance sur Mac vous permet d’accéder à des applications, ressources et bureaux Windows à partir de votre ordinateur Mac. Consultez les informations suivantes. Elles constituent un excellent point de départ. Et si vous avez des questions par la suite, n’hésitez pas à consulter notre [FAQ](remote-desktop-client-faq.md).

>[!NOTE]
> - Les nouvelles versions du client macOS vous intéressent ? Consultez [Nouveautés du Bureau à distance sur Mac](mac-whatsnew.md).
> - Le client Mac s’exécute sur les ordinateurs exécutant Mac OS 10.10 et versions ultérieures.
> - Les informations contenues dans cet article s’appliquent principalement à la version complète du client Mac (celle disponible dans l’App Store Mac). Testez les nouvelles fonctionnalités en téléchargeant la préversion de notre application ici : [Notes de mise à jour du client de la version bêta](https://go.microsoft.com/fwlink/?LinkID=619698&clcid=0x409).

## <a name="get-the-remote-desktop-client"></a>Obtenez le client Bureau à distance

Effectuez ces étapes pour bien démarrer avec le Bureau à distance sur votre appareil Mac:

1. Téléchargez le client Bureau à distance Microsoft à partir de l’[App Store Mac](https://itunes.apple.com/app/microsoft-remote-desktop/id1295203466?mt=12).
2. [Configurez votre PC pour accepter les connexions à distance](remote-desktop-client-faq.md#how-do-i-set-up-a-pc-for-remote-desktop). Si vous ignorez cette étape, vous ne pouvez pas vous connecter à votre PC.
3. Ajoutez une connexion Bureau à distance ou une ressource distante. Utilisez une connexion pour vous connecter directement à un PC Windows, et une ressource distante pour accéder à un programme RemoteApp, un bureau basé sur une session ou un bureau virtuel publié en local à l’aide de la fonctionnalité Connexions aux programmes RemoteApp et aux services Bureau à distance. Cette fonctionnalité est généralement disponible dans les environnements d’entreprise.

## <a name="what-about-the-mac-beta-client"></a>Présentation du client de la version bêta Mac

Nous testons de nouvelles fonctionnalités sur notre canal de préversion sur AppCenter. Vous voulez en savoir plus ? Rendez-vous sur la page [Bureau à distance Microsoft pour Mac](https://aka.ms/rdmacbeta) et sélectionnez **Télécharger**. Vous n’avez pas besoin de créer un compte ou de vous connecter à AppCenter pour télécharger le client de la version bêta.

Si vous avez déjà le client, vous pouvez vérifier si des mises à jour sont disponibles, pour être certain d’avoir la version la plus récente. En haut de la fenêtre du client de la version bêta, sélectionnez **Version bêta de Bureau à distance Microsoft**, puis **Rechercher des mises à jour**. 

## <a name="add-a-workspace"></a>Ajouter un espace de travail

Abonnez-vous au flux que votre administrateur vous a donné pour récupérer la liste des ressources managées disponibles sur votre appareil macOS.

Pour s’abonner à un flux :

1. Sélectionnez **Ajouter un flux** dans la page principale pour vous connecter au service et récupérer vos ressources.
2. Entrez l’URL du flux. Il peut s’agir d’une URL ou d’une adresse e-mail :
   - Si vous utilisez une URL, utilisez celle que votre administrateur vous a donnée. En règle générale, l’URL est <https://rdweb.wvd.microsoft.com>.
   - Pour utiliser l’e-mail, entrez votre adresse e-mail. Ceci indique au client de rechercher une URL associée à votre adresse e-mail si votre administrateur a configuré le serveur en ce sens.
3. Sélectionnez **S’abonner**.
4. Connectez-vous avec votre compte d’utilisateur quand vous y êtes invité.

Une fois que vous êtes connecté, la liste des ressources disponibles doit s’afficher.

Une fois que vous êtes abonné à un flux, son contenu est automatiquement mis à jour de façon régulière. Les ressources peuvent être ajoutées, changées ou supprimées en fonction des modifications apportées par votre administrateur.

### <a name="export-and-import-connections"></a>Exporter et importer des connexions

Vous pouvez exporter une définition de la connexion Bureau à distance et l’utiliser sur un autre appareil. Les Bureaux à distance sont enregistrés dans des fichiers .RDP distincts.

1. Dans le Centre de connexion, faites un clic droit sur le Bureau à distance.
2. Sélectionnez **Exporter**.
3. Accédez à l’emplacement où vous souhaitez enregistrer le fichier .RDP du Bureau à distance.
4. Sélectionnez **OK**.

Suivez cette procédure pour importer un fichier .RDP de Bureau à distance :

1. Dans la barre de menus, sélectionnez **Fichier** > **Importer**.
2. Accédez au fichier .RDP.
3. Sélectionnez **Ouvrir**.

## <a name="add-a-remote-resource"></a>Ajouter une ressource distante

Les ressources distantes peuvent être des programmes RemoteApp, des bureaux basés sur une session et des bureaux virtuels publiés à l’aide de la fonctionnalité Connexions aux programmes RemoteApp et aux services Bureau à distance.

- L’URL affiche le lien vers le serveur d’accès Web des services Bureau à distance qui vous donne accès aux connexions RemoteApp et Bureau à distance.
- Les connexions RemoteApp et Bureau à distance configurées sont affichées.

Pour ajouter une ressource distante :

1. Dans le Centre de connexion, sélectionnez **+** , puis **Ajouter des ressources distantes**. 
2. Entrez les informations appropriées pour la ressource distante :
   - **URL de flux** : URL du serveur d’accès web des services Bureau à distance. Vous pouvez également entrer votre compte e-mail professionnel dans ce champ : cela indique au client de rechercher le serveur d’accès Web des services Bureau à distance qui est associé à votre adresse e-mail.
   - **Nom d’utilisateur** : nom d’utilisateur à spécifier pour le serveur d’accès web des services Bureau à distance auquel vous vous connectez.
   - **Mot de passe** : mot de passe à spécifier pour le serveur d’accès web des services Bureau à distance auquel vous vous connectez.
3. Sélectionnez **Enregistrer**.

Les ressources distantes ajoutées seront affichées dans le Centre de connexion.

## <a name="connect-to-an-rd-gateway-to-access-internal-assets"></a>Se connecter à une passerelle Bureau à distance pour accéder aux ressources internes

Une passerelle Bureau à distance vous permet de vous connecter à un ordinateur distant sur un réseau d’entreprise à partir de n’importe où sur Internet. Vous pouvez créer et gérer vos passerelles dans les préférences de l’application ou lors de l’établissement d’une nouvelle connexion Bureau.

Pour configurer une nouvelle passerelle dans les préférences :

1. Dans le Centre de connexion, sélectionnez **Préférences > Passerelles**. 
2. Sélectionnez le bouton **+** situé en bas de la table, puis entrez les informations suivantes :
   - **Nom du serveur** : nom de l’ordinateur que vous souhaitez utiliser comme passerelle. Cela peut être un nom d’ordinateur Windows, un nom de domaine Internet ou une adresse IP. Vous pouvez aussi ajouter les informations de port au nom du serveur (par exemple : **RDGateway:443** ou **10.0.0.1:443**).
   - **Nom d’utilisateur** : nom d’utilisateur et mot de passe à spécifier pour la passerelle Bureau à distance à laquelle vous vous connectez. Vous pouvez également sélectionner **Utiliser les informations d’identification de la connexion** si vous préférez garder les mêmes nom d’utilisateur et mot de passe que ceux utilisés pour la connexion Bureau à distance.

## <a name="manage-your-user-accounts"></a>Gérer vos comptes d’utilisateur

Quand vous vous connectez à un bureau ou à des ressources distantes, vous pouvez enregistrer les comptes d’utilisateur pour les resélectionner ultérieurement. Vous pouvez gérer vos comptes d’utilisateur à l’aide du client Bureau à distance.

Pour créer un compte d’utilisateur :

1. Dans le Centre de connexion, sélectionnez **Paramètres** > **Comptes**.
2. Sélectionnez **Ajouter un compte d’utilisateur**.
3. Entrez les informations suivantes :
   - **Nom d’utilisateur** : nom d’utilisateur à enregistrer pour l’utiliser avec une connexion à distance. Entrez le nom d’utilisateur dans un de ces formats : nom_utilisateur, domaine\nom_utilisateur ou user_name@domain.com.
   - **Mot de passe** : mot de passe associé à l’utilisateur spécifié. Chaque compte d’utilisateur que vous souhaitez enregistrer pour les connexions à distance doit avoir un mot de passe associé.
   - **Nom convivial** : si vous utilisez le même compte d’utilisateur avec des mots de passe différents, définissez un nom convivial pour distinguer ces comptes d’utilisateurs.
4. Sélectionnez **Enregistrer**, puis **Paramètres**.

## <a name="customize-your-display-resolution"></a>Personnaliser la résolution de votre périphérique d’affichage

Vous pouvez spécifier la résolution du périphérique d’affichage de votre session Bureau à distance.

1. Dans le Centre de connexion, sélectionnez **Préférences**.
2. Sélectionnez **Resolution**.
3. Sélectionnez **+** .
4. Entrez une hauteur et une largeur de résolution, puis sélectionnez **OK**.

Pour supprimer la résolution, sélectionnez-la, puis sélectionnez **-** .

**Les périphériques d’affichage ont des espaces séparés** : si vous exécutez Mac OS X 10.9 et que vous avez désactivé **Les périphériques d’affichage ont des espaces séparés** dans Mavericks (**Préférences système > Contrôle des missions**), vous devez configurer ce paramètre dans le client Bureau à distance en utilisant la même option.

### <a name="drive-redirection-for-remote-resources"></a>Redirection de lecteur pour les ressources distantes

La redirection de lecteur est prise en charge pour les ressources distantes, de sorte que vous pouvez enregistrer les fichiers créés avec une application distante localement sur votre Mac. Le dossier redirigé est toujours votre répertoire personnel affiché en tant que lecteur réseau dans la session à distance.

> [!NOTE]
> Pour utiliser cette fonctionnalité, l’administrateur doit définir les paramètres appropriés sur le serveur.

## <a name="use-a-keyboard-in-a-remote-session"></a>Utiliser un clavier dans une session à distance

Les dispositions du clavier Windows diffèrent des dispositions du clavier Mac. 

- La touche Commande du clavier Mac correspond à la touche Windows.
- Pour effectuer des actions qui utilisent la touche Commande sur le Mac, vous devez utiliser la touche Ctrl (Contrôle) dans Windows. Par exemple : Copier = Ctrl + C.
- Les touches de fonction peuvent être activés dans la session en pressant également la touche Fn (par exemple : Fn + F1).
- La touche Alt située à droite de la barre d’espace sur le clavier Mac correspond à la touche Alt Gr/Alt droite dans Windows.

Par défaut, la session à distance utilisera les mêmes paramètres régionaux de clavier que le système d’exploitation sur lequel vous exécutez le client. Si votre Mac est en cours d’exécution sur un système d’exploitation EN-US (Anglais des États-Unis), cette langue est aussi utilisée pour les sessions à distance. Si les paramètres régionaux du clavier du système d’exploitation ne sont pas utilisés, vérifiez le paramètre du clavier sur le PC distant et modifiez-le manuellement. Si vous souhaitez obtenir davantage d’informations sur les claviers et les paramètres régionaux, veuillez consulter le [Forum aux questions du client Bureau à distance](remote-desktop-client-faq.md).

## <a name="support-for-remote-desktop-gateway-pluggable-authentication-and-authorization"></a>Prise en charge de l’autorisation et de l’authentification enfichables de la passerelle des services Bureau à distance

Windows Server 2012 R2 a introduit la prise en charge d’une nouvelle méthode d’authentification, l’autorisation et l’authentification enfichables de la passerelle des services Bureau à distance, qui offre plus de souplesse pour les routines d’authentification personnalisée. Vous pouvez maintenant essayer ce modèle d’authentification avec le client Mac. 

> [!IMPORTANT]
> Les modèles d’authentification et d’autorisation personnalisés avant Windows 8.1 ne sont pas pris en charge, bien que l’article ci-dessus les évoque.

Pour en savoir plus sur cette fonctionnalité, veuillez consulter la page [https://aka.ms/paa-sample](https://aka.ms/paa-sample).

> [!TIP]
> Vos questions et vos commentaires sont toujours les bienvenus. Toutefois, merci de ne pas utiliser la fonctionnalité de commentaire qui figure à la fin de cet article pour nous envoyer une demande d’aide. Veuillez plutôt accéder au [forum du client Bureau à distance](https://social.technet.microsoft.com/forums/windowsserver/en-us/home?forum=winrdc) et démarrez un nouveau fil de discussion. Vous souhaitez nous suggérer une fonctionnalité ? N’hésitez pas à utiliser le [forum UserVoice pour le client](https://remotedesktop.uservoice.com/forums/272085-remote-desktop-for-android) afin de nous en faire part.
