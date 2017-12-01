---
title: "Étapes de workflow DevOps boucle externe pour une application de Docker"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 070d174cde9e80f542865f5617b1c702a07a8018
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Étapes de workflow DevOps boucle externe pour une application de Docker

Figure 5-1 présente une description de bout en bout des étapes comprenant le flux de travail DevOps boucle externe.

![](./media/image1.png)

Flux de travail de la figure 5-1 : DevOps boucle externe pour les applications de Docker avec des outils Microsoft

Maintenant, nous allons examiner chacune de ces étapes en détail.

## <a name="step-1-inner-loop-development-workflow"></a>Étape 1 : Processus de développement de la boucle interne

Cette étape est expliquée en détail dans le chapitre 4, mais, pour résumer, voici où la boucle externe commence, le moment auquel un développeur exécute un push de code pour le système de gestion de contrôle de source (comme Git) initiation d’actions de pipeline de l’élément de configuration.

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>Étape 2 : L’intégration du contrôle de Code Source et la gestion avec Visual Studio Team Services et Git

À cette étape, vous devez disposer d’un système de contrôle de version pour collecter une version consolidée de tout le code provenant des différents développeurs de l’équipe.

Même si le contrôle de code source (SCC) et de gestion de code source peuvent sembler à la plupart des développeurs, lors de la création d’applications de Docker dans une durée de vie DevOps cycle seconde-nature, il est essentiel de souligner que vous ne devez pas envoyer les images Docker avec l’application directement dans le Registre de Docker global (comme le Registre de conteneur Azure ou le Hub d’ancrage) à partir de l’ordinateur du développeur. En revanche, les images Docker être libéré et déployées sur des environnements de production doivent être créés uniquement sur le code source qui sont intégré dans votre build global ou d’un pipeline de l’élément de configuration en fonction de votre référentiel de code source (comme Git).

Les images locales générées par les développeurs eux-mêmes doivent être utilisés uniquement par les développeurs lors du test au sein de leurs propres ordinateurs. C’est pourquoi il est essentiel pour que le pipeline DevOps activé à partir du code de contrôle de code source.

Visual Studio Team Services et Team Foundation Server prend en charge Git et Team Foundation Version Control. Vous pouvez choisir entre eux et l’utiliser pour une expérience de Microsoft de bout en bout. Toutefois, vous pouvez également gérer votre code dans des référentiels externes (tels que GitHub, les référentiels Git locaux ou Subversion) et toujours être en mesure de s’y connecter et obtenir le code comme point de départ pour votre pipeline de l’élément de configuration DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>Étape 3 : Build, l’élément de configuration, intégrer et tester avec Visual Studio Team Services et Docker

L’élément de configuration est devenue une norme pour le test de logiciels modernes et de remise. La solution de Docker gère une séparation nette entre les équipes de développement et les opérations. Immuabilité des images Docker permet de garantir un déploiement reproductible entre ce qui a développé, testé via l’élément de configuration et exécuter en production. Moteur docker déployé sur les ordinateurs portables développeur et infrastructure de test rend les conteneurs portable dans des environnements.

À ce stade, une fois que vous avez un système de contrôle de version avec le code correct soumis, vous avez besoin une *service de build* pour récupérer le code et exécuter le build global et les tests.

Le flux de travail interne pour cette étape (l’élément de configuration, build, de test) est sur la construction d’un pipeline de l’élément de configuration consistant à votre référentiel de code (Git, etc.), votre serveur de builds (Visual Studio Team Services), moteur Docker et un Registre Docker.

Vous pouvez utiliser Visual Studio Team Services comme base pour la création de vos applications et la définition de votre pipeline de l’élément de configuration et pour la publication des génération « artefacts » pour un « référentiel d’artefacts, » qui est expliqué dans l’étape suivante.

Lors de l’utilisation de Docker pour le déploiement, les « artefacts finals » pour le déploiement sont les images Docker avec votre application ou les services incorporées dans les. Ces images sont envoyées ou publiés sur un *Docker Registre* (référentiel privé, comme ceux que vous pouvez avoir dans le Registre de conteneur Azure ou une publique comme registre Docker Hub, qui est couramment utilisé pour les images de base officiels).

Voici le concept de base : l’élément de configuration du pipeline sera exclu-désactivée par une validation à un référentiel de contrôle de code source comme Git. La validation entraîne Visual Studio Team Services exécuter une tâche de build dans un conteneur Docker et, en cas de réussite de ce travail, distribuer une image Docker dans le Registre Docker, comme illustré dans la Figure 5-2.

![](./media/image2.png)

Figure 5-2 : les étapes impliquées dans l’élément de configuration

Voici les étapes de flux de travail de l’élément de configuration base avec Docker et Visual Studio Team Services :

1.  Le développeur exécute un push d’une validation à un référentiel de contrôle de code source (Git/Visual Studio Team Services, GitHub, etc.).

2.  Si vous utilisez Visual Studio Team Services ou Git, l’élément de configuration intégrée, ce qui signifie qu’il est aussi simple que la sélection d’une case à cocher dans Visual Studio Team Services. Si vous utilisez un contrôle de code source externe (par exemple, GitHub), un *webhook* sera de notifier Visual Studio Team Services de la mise à jour ou de type push vers Git/GitHub.

3.  Visual Studio Team Services extrait du référentiel de contrôle de code source, y compris le fichier DockerFile décrivant l’image, ainsi que le code d’application et de test.

4.  Visual Studio Team Services génère une image Docker et le marque en avec un numéro de build.

5.  Visual Studio Team Services instancie le conteneur Docker dans l’hôte Docker mis en service et exécute les tests appropriés.

6.  Si les tests réussissent, l’image est tout d’abord un nouveau libellée à un nom explicite afin que vous sachiez il s’agit d’une « build privilégiée » (tels que « / 1.0.0 » ou n’importe quel autre étiquette) et ensuite transmis à votre Registre Docker (Docker Hub, Registre de conteneur Azure, DTR, etc.).

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Mise en œuvre le pipeline de l’élément de configuration avec Visual Studio Team Services et l’extension Docker pour Visual Studio Team Services

Le [extension Visual Studio Team Services Docker](https://aka.ms/vstsdockerextension) ajoute une tâche à votre pipeline de l’élément de configuration avec laquelle vous pouvez créer des images de Docker, push Docker images dans un Registre Docker authentifié, exécutez Docker images ou exécuter d’autres opérations offertes par le Docker CLI. Il ajoute également une tâche Docker Compose que vous pouvez utiliser pour créer, transmettre et exécuter des applications de Docker multicontainer ou exécuter d’autres opérations offertes par la CLI composer Docker, comme indiqué dans la Figure 5-3.

![](./media/image3.png)

Figure 5-3 : le pipeline de l’élément de configuration Docker dans Visual Studio Team Services

L’extension Docker pouvez utiliser des points de terminaison de service pour les ordinateurs hôtes de Docker et pour que les registres de l’image ou du conteneur. La valeur par défaut de tâches à l’aide d’un hôte Docker local s’il est disponible (cela actuellement requiert un agent de Visual Studio Team Services personnalisé) ; dans le cas contraire, ils nécessitent que vous fournissez une connexion d’hôte Docker. Les actions qui dépendent d’authentifié avec un Registre Docker, par exemple en exécutant un push d’une image, nécessitent que vous fournissiez une Docker connexion du Registre.

L’extension de Visual Studio Team Services Docker installe les composants suivants dans votre compte Visual Studio Team Services :

-   Un point de terminaison de service pour se connecter à un Registre Docker

-   Un point de terminaison de service pour se connecter à un hôte de conteneur Docker

-   Une tâche de Docker pour effectuer les opérations suivantes :

-   Créer une image

-   Distribuer une image ou un référentiel à un Registre

-   Exécuter une image dans un conteneur

-   Exécuter une commande Docker

-   Une tâche Docker Compose pour exécuter une commande Docker Compose

Avec ces tâches Visual Studio Team Services, une build Docker de Linux/machine virtuelle d’hôte mis en service dans Azure et votre Registre Docker préféré (Registre de conteneur Azure, Docker Hub, privé Docker DTR ou tout autre registre Docker), vous pouvez assembler votre pipeline de l’élément de configuration de Docker dans un très cohérente.

***Configuration requise :***

-   Visual Studio Team Services, ou pour les installations locales, Team Foundation Server 2015 Update 3 ou version ultérieure.

-   Un agent de Visual Studio Team Services contenant les fichiers binaires de Docker.

Il est un moyen simple de créer un de ces Docker permet d’exécuter un conteneur en fonction de l’image de Docker de l’agent de Visual Studio Team Services.

**Plus d’informations** pour en savoir plus sur l’assemblage un Visual Studio Team Services Docker l’élément de configuration de pipeline et que vous pour afficher les procédures pas à pas, visitez les sites suivants :

Exécution d’un agent de Visual Studio Team Services comme un conteneur Docker : [https://hub.docker.com/r/ \ vsts/microsoft-agent /](https://hub.docker.com/r/microsoft/vsts-agent/)

Extension Docker de VSTS : <https://aka.ms/vstsdockerextension>

Création d’images de .NET Core Linux Docker avec Visual Studio Team Services : <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Création d’un basés sur Linux Service Visual Studio Team build ordinateur avec prise en charge Docker : <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Intégrer, tester et valider des applications de Docker multicontainer

En règle générale, la plupart des applications de Docker sont composées de plusieurs conteneurs plutôt qu’un seul conteneur. Un bon exemple est une application microservices pour lequel vous aurait un conteneur par microservice. Toutefois, même sans en suivant les modèles d’approche microservices, il est très probable que votre application de Docker est composée de plusieurs conteneurs ou les services.

Par conséquent, après avoir généré les conteneurs d’applications dans le pipeline de l’élément de configuration, vous devez également déployer, intégrer et tester l’application dans son ensemble avec tous ses conteneurs au sein d’un hôte Docker d’intégration ou même dans un cluster de test qui sont vos conteneurs distribué.

Si vous utilisez un seul ordinateur hôte, vous pouvez utiliser les commandes Docker tels que docker-composer pour générer et déployer des conteneurs connexes pour tester et valider l’environnement de Docker dans une seule machine virtuelle. Toutefois, si vous travaillez avec un cluster orchestrator comme contrôleur de domaine/système d’exploitation, Kubernetes ou Docker Swarm, vous devez déployer vos conteneurs via un mécanisme différent ou un orchestrator, en fonction de votre cluster/planificateur sélectionné.

Voici plusieurs types de tests que vous pouvez exécuter sur des conteneurs Docker :

-   Tests unitaires pour les conteneurs Docker

-   Test des groupes d’applications reliées entre elles ou microservices

-   Dans les versions de production et « contrôle de validité » de test

Le point important est que lors de l’exécution d’intégration et les tests fonctionnels, vous devez exécuter ces tests à partir d’en dehors des conteneurs. Tests ne doivent pas être définis et s’exécutent dans les conteneurs que vous déployez, étant donné que les conteneurs sont basées sur des images statiques doivent être exactement comme ceux que vous comptez déployer en production.

Une option très envisageable lorsque vous testez des scénarios plus avancés tels que le test (test de cluster, cluster intermédiaire et le cluster de production) de plusieurs clusters consiste à publier des images à un Registre à tester dans différents clusters.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Distribuer l’image de Docker application personnalisée dans votre Registre Docker global

Une fois les images Docker ont été testées et validées, que vous souhaitez marquer et de les publier dans votre Registre Docker. Le Registre Docker est un élément critique dans le cycle de vie des applications de Docker, car il est l’emplacement central où vous stockez votre test personnalisé (également appelé « images privilégiés ») à être déployé dans les environnements d’assurance qualité et de production.

Similaire à la façon dont le code d’application stocké dans votre référentiel de contrôle de code source (Git, etc.) est « votre source de vérité », le Registre Docker est votre « source de vérité » pour votre application binaire ou les bits pour le déploiement sur les environnements de production ou des questions et réponses.

En règle générale, vous pouvez souhaiter avoir vos référentiels privés pour vos images personnalisées dans un référentiel privé dans le Registre de conteneur Azure ou dans un registre locale comme le Registre de Docker approuvé ou dans un registre public-cloud avec un accès limité (par exemple Hub docker), bien que dans ce dernier cas, si votre code n’est pas open source, vous devez approuver la sécurité du fournisseur. Dans les deux cas, la méthode par laquelle vous cela est assez similaire et enfin en fonction de la commande docker, comme illustré dans la Figure 5-4.

![](./media/image4.png)

Figure 5-4 : publication d’images personnalisées dans le Registre de Docker

Il existe plusieurs offres des registres de Docker à partir des fournisseurs de cloud comme Azure conteneur de Registre, Registre de conteneur Amazon Web Services, Registre de conteneur de Google, quai Registre et ainsi de suite.

À l’aide de l’extension de Visual Studio Team Services Docker, vous pouvez transmettre un ensemble d’images de service défini par un fichier compose.yml de docker, avec plusieurs balises à un Registre Docker authentifié (par exemple, le Registre de conteneur Azure), comme indiqué dans la Figure 5-5.

![](./media/image5.png)

Figure 5-5 : à l’aide de Visual Studio Team Services pour la publication des images personnalisées à un Registre Docker

**Plus d’informations** pour en savoir plus sur l’extension Docker pour Visual Studio Team Services, accédez à <https://aka.ms/vstsdockerextension>. Pour en savoir plus sur le Registre de conteneur Azure, accédez à <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Étape 4 : CD, déployer

Immuabilité des images Docker permet de garantir un déploiement reproductible avec ce qui a développé, testé via l’élément de configuration et exécuter en production. Après avoir configuré les images de Docker application publiées dans votre Registre Docker (privée ou publique), vous pouvez les déployer pour les environnements plusieurs dont vous disposez (production, les questions et réponses, de mise en lots, etc.) à partir de votre pipeline de CD à l’aide de Visual Studio Team Services tâches du pipeline ou Visual Studio Team Services Release Management.

Toutefois, à ce stade il varie selon le type d’application de Docker que vous déployez. Déploiement simple d’une application (à partir d’un point de vue composition et de déploiement) comme un monolithique application comprenant plusieurs conteneurs ou les services et déployé plusieurs serveurs ou ordinateurs virtuels est très différente de déploiement d’une application plus complexe, comme un applications avec les fonctionnalités démultipliée orientée vers microservices. Ces deux scénarios sont expliqués dans les sections suivantes.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Déploiement composé applications Docker dans plusieurs environnements de Docker

Regardons premièrement le scénario moins complexes : déploiement vers les hôtes Docker simples (machines virtuelles ou serveurs) dans un environnement unique ou plusieurs environnements (questions et réponses, intermédiaire et production). Dans ce scénario, en interne le pipeline de votre CD-ROM peut utiliser docker-composer (à partir de vos tâches de déploiement de Visual Studio Team Services) pour déployer les applications de Docker avec son ensemble des conteneurs ou des services, comme illustré dans la Figure 5-6.

![](./media/image6.png)

Figure 5-6 : déploiement de conteneurs d’applications dans le Registre des environnements de hôte simple Docker

Figure 5-7 met en évidence la façon dont vous pouvez vous connecter votre élément de configuration de build dans les environnements de test/AQ via Visual Studio Team Services en cliquant sur Docker Compose dans la boîte de dialogue Ajouter une tâche. Cependant, lors du déploiement dans les environnements de production ou intermédiaire, vous utilisez généralement les fonctionnalités de gestion des versions gère plusieurs environnements (comme les questions et réponses, intermédiaire et production). Si vous déployez vers les hôtes Docker uniques, il est à l’aide de Visual Studio Team Services « Docker Compose » la tâche (ce qui revient à appeler la docker-composer commande sous le capot). Si vous déployez dans le Service de conteneur Azure, il utilise la tâche de déploiement de Docker, comme expliqué dans la section suivante.

![](./media/image7.png)

Figure 5-7 : ajout d’une tâche Docker Compose dans un pipeline de Visual Studio Team Services

Lorsque vous créez une version de Visual Studio Team Services, il prend un ensemble d’artefacts d’entrée. Elles sont destinées à être immuable pendant toute la durée de vie de la version dans différents environnements. Lorsque vous introduisez des conteneurs, les artefacts d’entrée identifient des images dans un Registre à déployer. Selon la façon dont ils ont été identifiés, ils ne sont pas garanties reste la même pendant toute la durée de la version, le cas le plus évident en cours lorsque vous faites référence à « myimage:latest » à partir d’un fichier docker-compose.

L’extension Docker pour Visual Studio Team Services vous donne la possibilité de générer des artefacts de build qui contient l’image de Registre spécifiques des résumés garantis pour identifier de façon unique la même image binaire. Voici ce que vous souhaitez utiliser comme entrée pour une mise en production.

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>La gestion des versions dans les environnements de Docker à l’aide de Visual Studio Team Services Release Management

Via les extensions Visual Studio Team Services, vous pouvez générer une nouvelle image, publier sur un Registre Docker, exécutez-le sur les ordinateurs hôtes Windows ou Linux et utiliser des commandes telles que docker-composer pour déployer plusieurs conteneurs en tant qu’une application entière, à l’aide de l’élément visuel Fonctionnalités de gestion de version Team Services Studio destinées à plusieurs environnements, comme indiqué dans la Figure 5-8.

![](./media/image8.png)

Figure 5 à 8 : configuration de Visual Studio Team Services Docker Compose de tâches à partir de Visual Studio Team Services Release Management

Toutefois, gardez à l’esprit que le scénario illustré dans la Figure 5-6 et implémentée dans la Figure 5-8 est assez basique (qu’il déploie vers les hôtes Docker simples et machines virtuelles, et il y aura un conteneur unique ou une instance par image) et probablement doit être utilisé uniquement pour le développement ou test sc Gestionnaire de scénarios. Dans la plupart des scénarios de production d’entreprise, vous pourriez avoir haute disponibilité (HA) et à gérer l’évolutivité en équilibrant la charge entre plusieurs nœuds, serveurs et les machines virtuelles, ainsi que « basculements intelligents » ainsi que si un serveur ou un nœud tombe en panne, ses services et conteneurs seront déplacés vers un autre serveur hôte ou une machine virtuelle. Dans ce cas, vous avez besoin des technologies plus avancées telles que les clusters de conteneur, orchestrators et des planificateurs. Par conséquent, la méthode de déploiement pour les clusters est précisément via des scénarios avancés expliquées dans la section suivante.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Déploiement d’applications Docker complexes à des clusters Docker (contrôleur de domaine/système d’exploitation, Kubernetes et Docker Swarm)

La nature des applications distribuées nécessite des ressources de calcul qui sont également distribuées. Pour que les capacités de production à l’échelle, vous devez disposer de fonctionnalités qui fournissent une haute évolutivité de clustering et haute disponibilité en fonction des ressources regroupées.

Vous pouvez déployer des conteneurs manuellement dans ces clusters à partir d’un outil CLI tels que Docker Swarm (comme à l’aide de [de création du service de docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) ou une interface utilisateur web tels que [mésosphère Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) pour le contrôleur de domaine/système d’exploitation clusters, mais vous devez réserver qui uniquement pour tester le déploiement de veille ou à des fins de gestion telles que l’évolution horizontale ou à des fins d’analyse.

À partir d’un point de vue de CD et Visual Studio Team Services en particulier, vous pouvez exécuter les tâches de déploiement spécialement faite vos environnements de Visual Studio Team Services Release Management, qui vous allez déployer vos applications en conteneur pour les clusters répartis dans Service de conteneur, comme illustré dans la Figure 5-9.

![](./media/image9.png)

Figure 5-9 : déploiement d’applications distribuées au Service de conteneur

Au départ, lors du déploiement de clusters ou orchestrators, vous traditionnellement utiliseriez mécanismes par chaque orchestrator (autrement dit, mésosphère contrôleur de domaine/système d’exploitation ou Kubernetes ont des mécanismes de déploiement différents à Docker et Docker et les scripts de déploiement spécifique Swarm) au lieu de la plus simple et facile à utiliser docker-composent des outil basé sur le fichier de définition de compose.yml de docker. Toutefois, grâce à la tâche de Microsoft Visual Studio Team Services Docker Deploy montre la Figure 5-10, vous pouvez à présent également déployer au contrôleur de domaine/système d’exploitation en utilisant simplement votre fichier docker-compose.yml familière, car Microsoft effectue cette traduction « » pour vous (à partir de votre fichier compose.yml de docker dans d’autres formats requis par le contrôleur de domaine/OS).

![](./media/image10.png)

Figure 5-10 : ajout de la tâche de déploiement de Docker à RM de votre environnement

Figure 5-11 montre comment vous pouvez modifier la tâche de déploiement de Docker et spécifier le Type de cible (conteneur Service de contrôleur de domaine/système d’exploitation Azure, dans ce cas), votre fichier de composer Docker et la connexion Docker Registre (par exemple, le Registre de conteneur Azure ou le Hub d’ancrage). Il s’agit de la tâche récupère où vos images Docker personnalisées de prêt à l’emploi pour être déployé en tant que conteneurs dans le cluster de contrôleur de domaine/système d’exploitation.

![](./media/image11.png)

Déploiement de la figure 5-11 : déployer de Docker tâche définition pour le Service de conteneur Azure DC/OS

**Plus d’informations** pour en savoir plus sur le pipeline de CD avec Visual Studio Team Services et Docker, visitez les sites suivants :

Extension Studio Team Services Visual pour Docker et le Service de conteneur Azure : [https://aka.ms/ \ vstsdockerextension](https://aka.ms/vstsdockerextension)

Service de conteneur Azure : <https://aka.ms/azurecontainerservice>

Contrôleur de domaine mésosphère/OS : <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Étape 5 : Exécuter et gérer

En cours d’exécution et la gestion des applications en production de l’entreprise au niveau du est un sujet principal dans de lui-même et en raison du type d’opérations et les personnes travaillant à ce niveau (informatiques), ainsi que l’étendue de grande taille de cette zone, nous avons consacré l’ensemble suivant chapitre expliquant il.

## <a name="step-6-monitor-and-diagnose"></a>Étape 6 : Analyser et de diagnostic

Cette rubrique également est décrite dans le chapitre suivant dans le cadre des tâches qui effectue des opérations informatiques dans les systèmes de production ; Toutefois, il est important de souligner que les informations obtenues lors de cette étape doivent flux à l’équipe de développement afin que l’application est améliorée en permanence. À partir de ce point de vue, il fait également partie de DevOps, bien que les tâches et les opérations sont généralement effectuées par informatique.

Uniquement lors de la surveillance et diagnostic est à 100 % dans le domaine du DevOps sont analytique effectuée par l’équipe de développement par rapport aux environnements de test ou de la version bêta et processus d’analyse. Pour cela, effectuez le test de charge ou simplement en version bêta ou les environnements de questions et réponses, où les testeurs bêta essayez les nouvelles versions d’analyse.

>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (.. /Run-Manage-Monitor-docker-Environments/index.MD)
