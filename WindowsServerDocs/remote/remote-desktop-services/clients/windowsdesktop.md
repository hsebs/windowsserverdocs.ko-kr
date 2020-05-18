---
title: Bien démarrer avec le client Windows Desktop
description: Informations de base sur le client Windows Desktop.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 04/28/2020
ms.localizationpriority: medium
ms.openlocfilehash: 368dc3889c5275512e345c26fcef504c6ceaa8c2
ms.sourcegitcommit: d06650cfab2972551c3a269b3271596f55c1bd3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82726707"
---
# <a name="get-started-with-the-windows-desktop-client"></a>Bien démarrer avec le client Windows Desktop

>S’applique à : Windows 10, Windows 10 IoT Entreprise et Windows 7

Vous pouvez utiliser le client Bureau à distance pour Windows Desktop afin d’accéder aux applications et aux appareils de bureau Windows à distance à partir d’un autre appareil Windows.

> [!NOTE]
> - Cette documentation ne concerne pas le client Connexion Bureau à distance (MSTSC) fourni avec Windows. Elle s’applique au client Bureau à distance (MSRDC).
> - Actuellement, ce client ne permet d’accéder aux applications et aux appareils de bureau Windows à distance qu’à partir de [Windows Virtual Desktop](https://aka.ms/wvd).
> - Vous êtes curieux de découvrir les nouvelles versions du client Windows Desktop ? Consultez [Nouveautés du client Windows Desktop](windowsdesktop-whatsnew.md).

## <a name="install-the-client"></a>Installer le client

Choisissez le client qui correspond à la version de Windows. Le nouveau client Bureau à distance (MSRDC) prend en charge les appareils clients Windows 10, Windows 10 IoT Entreprise et Windows 7.

- [Windows 64 bits](https://go.microsoft.com/fwlink/?linkid=2068602)
- [Windows 32 bits](https://go.microsoft.com/fwlink/?linkid=2098960)
- [Windows ARM64](https://go.microsoft.com/fwlink/?linkid=2098961)

Vous pouvez installer le client pour l’utilisateur actuel, ce qui ne nécessite pas de droits d’administrateur, ou votre administrateur peut installer et configurer le client afin que tous les utilisateurs de l’appareil puissent y accéder.

Une fois le client installé, vous pouvez le lancer à partir du menu Démarrer en recherchant **Bureau à distance**.

## <a name="update-the-client"></a>Mettre à jour le client

Tant que votre administrateur ne désactive pas les notifications, vous êtes averti chaque fois qu’une nouvelle version du client est disponible. La notification s’affiche dans le Centre de connexion ou dans le Centre de notifications Windows. Pour mettre à jour votre client, il vous suffit de sélectionner la notification.

Vous pouvez également rechercher manuellement les nouvelles mises à jour du client :

1. Dans le Centre de connexion, appuyez sur le menu de dépassement ( **...** ) dans la barre de commandes en haut du client.
2. Sélectionnez **À propos de** dans le menu déroulant.
3. Le client recherche automatiquement les mises à jour.
4. Si une mise à jour est disponible, appuyez sur **Installer la mise à jour** pour mettre à jour le client.

## <a name="workspaces"></a>Espaces de travail

Vous pouvez obtenir la liste des ressources managées auxquelles vous pouvez accéder, notamment les applications et les appareils de bureau, en vous abonnant à l’espace de travail fourni par votre administrateur. Quand vous vous abonnez, les ressources deviennent disponibles sur votre ordinateur local. Le client Windows Desktop prend actuellement en charge les ressources publiées à partir de Windows Virtual Desktop.

### <a name="subscribe-to-a-workspace"></a>S’abonner à un espace de travail

1. Dans la page principale du client, également appelée Centre de connexion, cliquez sur **S’abonner**.
2. Connectez-vous avec votre compte d’utilisateur quand vous y êtes invité.
3. Les ressources qui apparaissent dans le Centre de connexion sont regroupées par espace de travail.

Pour lancer des ressources, utilisez l’une des méthodes suivantes :

- Accédez au Centre de connexion, puis double-cliquez sur une ressource pour la lancer.
- Vous pouvez également accéder au menu Démarrer et rechercher un dossier avec le nom de l’espace de travail ou entrer le nom de la ressource dans la barre de recherche.

### <a name="workspace-details"></a>Détails de l’espace de travail

Une fois abonné, vous pouvez afficher des informations supplémentaires sur un espace de travail dans le panneau Détails :

- Nom de l’espace de travail
- URL et nom d’utilisateur utilisés pour s’abonner
- Nombre d’applications et d’appareils de bureau
- Date/heure de la dernière actualisation
- État de la dernière actualisation

Accès au panneau Détails :

1. Dans le Centre de connexion, appuyez sur le menu de dépassement ( **...** ) à côté de l’espace de travail.
2. Sélectionnez **Détails** dans le menu déroulant.
3. Le panneau Détails s’affiche sur le côté droit du client.

Une fois que vous êtes abonné, l’espace de travail est automatiquement actualisé à intervalles réguliers. Les ressources peuvent être ajoutées, changées ou supprimées en fonction des modifications apportées par votre administrateur.

Vous pouvez également rechercher manuellement les mises à jour des ressources si nécessaire en sélectionnant **Actualiser** dans le panneau Détails.

### <a name="refreshing-a-workspace"></a>Actualisation d’un espace de travail

Vous pouvez actualiser manuellement un espace de travail en sélectionnant **Actualiser** dans le menu de dépassement ( **...** ) à côté de l’espace de travail.

### <a name="unsubscribe-from-a-workspace"></a>Se désabonner d’un espace de travail

Cette section vous apprend à vous désabonner d’un espace de travail. Vous pouvez vous désabonner pour vous réabonner avec un autre compte ou supprimer vos ressources du système.

1. Dans le Centre de connexion, appuyez sur le menu de dépassement ( **...** ) à côté de l’espace de travail.
2. Dans le menu déroulant, sélectionnez **Se désabonner**.
3. Passez en revue la boîte de dialogue et sélectionnez **Continuer**.

## <a name="managed-desktops"></a>Bureaux gérés

Les espaces de travail peuvent contenir plusieurs ressources gérées, notamment des bureaux. Quand vous accédez à un bureau géré, vous avez accès à toutes les applications installées par votre administrateur.

### <a name="desktop-settings"></a>Paramètres du bureau

Vous pouvez configurer certains paramètres des ressources de bureau pour que l’expérience réponde à vos besoins. Pour accéder à la liste des paramètres disponibles, cliquez avec le bouton droit sur la ressource de bureau, puis sélectionnez **Paramètres**.

Le client utilise les paramètres configurés par votre administrateur, sauf si vous désactivez l’option **Utiliser les paramètres par défaut**. Dans ce cas, vous pouvez configurer les options suivantes :

- L’option **Configuration de l’affichage** sélectionne les affichages à utiliser pour la session ouverte et détermine les paramètres supplémentaires disponibles.
  - L’option **Tous les affichages** garantit que la session utilise toujours tous vos affichages locaux, même si certains d’entre eux sont ajoutés ou supprimés ultérieurement.
  - L’option **Monoaffichage** garantit que la session utilise toujours un seul affichage et vous permet de configurer ses propriétés.
  - L’option **Affichages spécifiques** vous permet de choisir les affichages à utiliser pour la session et fournit une option permettant de changer dynamiquement la liste des affichages au cours de la session.
- **Sélectionner les écrans à utiliser pour la session** spécifie les écrans locaux à utiliser pour la session. Tous les écrans sélectionnés doivent être adjacents. Ce paramètre n’est disponible qu’en mode **Affichages spécifiques**.
- L’option **Agrandir sur les affichages actifs** détermine les affichages utilisés par les sessions en mode plein écran. Quand elle est activée, la session passe en mode plein écran sur les affichages touchés par la fenêtre de session. Vous pouvez ainsi changer les affichages au cours de la session. Quand elle est désactivée, la session passe en mode plein écran dans les mêmes affichages sur lesquels elle se trouvait la dernière fois qu’elle était en mode plein écran. Ce paramètre n’est disponible qu’en mode **Affichages spécifiques**, sinon il est désactivé.
- L’option **Monoaffichage en mode fenêtré** détermine les affichages qui sont disponibles dans la session quand elle quitte le mode plein écran. Quand elle est activée, la session bascule vers un affichage unique en mode fenêtré. Quand elle est désactivée, la session conserve les mêmes affichages en mode fenêtré qu’en mode plein écran. Ce paramètre n’est disponible que dans les modes **Tous les affichages** et **Affichages spécifiques**, sinon il est désactivé.
- **Démarrer en plein écran** détermine si la session est lancée en mode plein écran ou en mode fenêtré. Ce paramètre n’est disponible qu’en mode **Monoaffichage**, sinon il est désactivé.
- **Ajuster la session à la fenêtre** détermine la façon dont la session est affichée quand la résolution du bureau à distance diffère de la taille de la fenêtre locale. Si cette option est activée, le contenu de la session est redimensionné pour tenir à l’intérieur de la fenêtre et les proportions de la session sont conservées. Si cette option est désactivée, des barres de défilement ou des zones noires apparaissent quand la résolution et la taille de la fenêtre ne correspondent pas. Ce paramètre est disponible dans tous les modes.
- **Mettre à jour la résolution en cas de redimensionnement** met automatiquement à jour la résolution du bureau à distance quand vous redimensionnez la session en mode fenêtré. Quand cette option est désactivée, la session reste toujours à la résolution que vous spécifiez dans **Résolution**. Ce paramètre n’est disponible qu’en mode **Monoaffichage**, sinon il est désactivé.
- **Résolution** vous permet de spécifier la résolution du bureau à distance. La session conserve cette résolution pendant toute sa durée. Ce paramètre est disponible uniquement en mode **Monoaffichage** et quand l’option **Mettre à jour la résolution en cas de redimensionnement** est désactivée.
- **Changer la taille du texte et des applications** permet de spécifier la taille du contenu de la session. Ce paramètre s’applique uniquement en cas de connexion à Windows 8.1 et ultérieur ou à Windows Server 2012 R2 et ultérieur. Ce paramètre est disponible uniquement en mode **Monoaffichage** et quand l’option **Mettre à jour la résolution en cas de redimensionnement** est désactivée.

## <a name="provide-feedback"></a>Fournir un commentaire

Vous souhaitez suggérer une fonctionnalité ou signaler un problème ? Dites-nous laquelle sur le [Hub de commentaires](feedback-hub://?tabid=2&contextid=883). Vous pouvez également accéder au hub de commentaires par le biais du client :

1. Dans le Centre de connexion, appuyez sur l’option **Envoyer des commentaires** dans la barre de commandes en haut du client pour ouvrir l’application Hub de commentaires.
2. Entrez les informations demandées dans les champs **Résumé** et **Détails**. Quand vous avez terminé, appuyez sur **Suivant**.
3. Indiquez s’il s’agit d’un **Problème** ou d’une **Suggestion**.
4. Vérifiez si la catégorie figure dans **Applications** > **Bureau à distance**. Si c’est le cas, appuyez sur **Suivant**.
5. Passez en revue les rubriques de commentaires existantes pour voir si quelqu’un d’autre a signalé le même problème. Si ce n’est pas le cas, sélectionnez **Créer un bogue**, puis appuyez sur **Suivant**.
6. La page suivante vous permet de donner davantage d’informations pour nous aider à résoudre le problème. Vous pouvez fournir plus de détails, envoyer des captures d’écran et même créer un enregistrement du problème pour nous montrer ce qui se passe. Pour créer un enregistrement, sélectionnez **Démarrer l’enregistrement**, puis effectuez les opérations ayant conduit au problème. Quand vous avez terminé, revenez au Hub de commentaires et sélectionnez **Arrêter l’enregistrement**.
7. Si vous êtes satisfait des informations fournies, appuyez sur **Envoyer**.
8. Dans la page « Merci pour vos commentaires ! », appuyez sur **Partager mes commentaires** pour générer un lien que vous pouvez partager avec d’autres utilisateurs au besoin.

### <a name="access-client-logs"></a>Accéder aux journaux du client

L’examen d’un problème peut vous amener à consulter les journaux du client.

Pour récupérer les journaux du client :

1. Assurez-vous qu’aucune session n’est active et que le processus client ne s’exécute pas en arrière-plan en cliquant avec le bouton droit sur l’icône **Bureau à distance** dans la barre d’état système et en sélectionnant **Déconnecter toutes les sessions**.
2. Ouvrez l’**Explorateur de fichiers**.
3. Accédez au dossier **%temp%\DiagOutputDir\RdClientAutoTrace**.
