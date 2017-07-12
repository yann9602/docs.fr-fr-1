

# [Microservices .NET : Architecture pour les applications .NET en conteneurs](index.md)


## [Introduction aux conteneurs et à Docker](container-docker-introduction/index.md)


### [Qu’est-ce que Docker ?](container-docker-introduction/docker-defined.md)


### [Terminologie Docker](container-docker-introduction/docker-terminology.md)


### [Conteneurs, images et registres Docker](container-docker-introduction/docker-containers-images-registries.md)


## [Choix entre .NET Core et .NET Framework pour les conteneurs Docker](net-core-net-framework-containers/index.md)


### [Recommandations générales](net-core-net-framework-containers/general-guidance.md)


### [Quand choisir .NET Core pour les conteneurs Docker](net-core-net-framework-containers/net-core-container-scenarios.md)


### [Quand choisir .NET Framework pour les conteneurs Docker](net-core-net-framework-containers/net-framework-container-scenarios.md)


### [Table de décision : Infrastructures .NET à utiliser pour Docker](net-core-net-framework-containers/container-framework-choice-factors.md)


### [Quel système d’exploitation cibler avec les conteneurs .NET](net-core-net-framework-containers/net-container-os-targets.md)


### [Images officielles de .NET Core Docker](net-core-net-framework-containers/official-net-docker-images.md)


## [Architecture d’applications conteneur et basées sur des microservices](architect-microservice-container-applications/index.md)


### [Placement d’applications monolithiques dans un conteneur](architect-microservice-container-applications/containerize-monolithic-applications.md)


### [État et données dans les applications de Docker](architect-microservice-container-applications/docker-application-state-data.md)


### [Architecture orientée service](architect-microservice-container-applications/service-oriented-architecture.md)


### [Architecture de microservices](architect-microservice-container-applications/microservices-architecture.md)


### [Souveraineté des données par microservice](architect-microservice-container-applications/data-sovereignty-per-microservice.md)


### [Architecture logique et architecture physique](architect-microservice-container-applications/logical-versus-physical-architecture.md)


### [Défis et solutions pour la gestion des données distribuée](architect-microservice-container-applications/distributed-data-management.md)


### [Identification des limites de modèle de domaine pour chaque microservice](architect-microservice-container-applications/identify-microservice-domain-model-boundaries.md)


### [Communication entre microservices](architect-microservice-container-applications/communication-between-microservices.md)


### [Communication basée sur des messages asynchrones](architect-microservice-container-applications/asynchronous-message-based-communication.md)


### [Création, évolution et gestion de version des API de microservices et des contrats](architect-microservice-container-applications/maintain-microservice-apis.md)


### [Adressabilité des microservices et Registre du service](architect-microservice-container-applications/microservices-addressability-service-registry.md)


### [Création d’une interface utilisateur composite basée sur des microservices, notamment la forme et la disposition de l’interface utilisateur visuelle générées par plusieurs microservices](architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)


### [Résilience et haute disponibilité dans les microservices](architect-microservice-container-applications/resilient-high-availability-microservices.md)


### [Orchestration des microservices et des applications à plusieurs conteneurs pour une grande scalabilité et une haute disponibilité](architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)


### [Utilisation d’Azure Service Fabric](architect-microservice-container-applications/using-azure-service-fabric.md)


## [Processus de développement des applications basées sur Docker](docker-application-development-process/index.md)


### [Flux de travail de développement des applications Docker](docker-application-development-process/docker-app-development-workflow.md)


## [Déploiement d’applications web .NET Core basées sur un seul conteneur sur des hôtes Linux ou Windows Nano Server](net-core-single-containers-linux-windows-server-hosts/index.md)


## [Migration d’applications .NET Framework monolithiques héritées vers des conteneurs Windows](containerize-net-framework-applications/index.md)


## [Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices](multi-container-microservice-net-applications/index.md)


### [Conception d’une application orientée microservice](multi-container-microservice-net-applications/microservice-application-design.md)


### [Création d’un microservice CRUD simple piloté par les données](multi-container-microservice-net-applications/data-driven-crud-microservice.md)


### [Définition de votre application à plusieurs conteneurs avec docker-compose.yml](multi-container-microservice-net-applications/multi-container-applications-docker-compose.md)


### [Utilisation d’un serveur de base de données s’exécutant en tant que conteneur](multi-container-microservice-net-applications/database-server-container.md)


### [Implémentation de la communication basée sur les événements entre les microservices (événements d’intégration)](multi-container-microservice-net-applications/integration-event-based-microservice-communications.md)


### [Implémentation d’un bus d’événements avec RabbitMQ pour l’environnement de développement ou de test](multi-container-microservice-net-applications/rabbitmq-event-bus-development-test-environment.md)


### [Abonnement à des événements](multi-container-microservice-net-applications/subscribe-events.md)


### [Test d’applications web et de services ASP.NET Core](multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md)


## [Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS](microservice-ddd-cqrs-patterns/index.md)


### [Application de modèles CQRS et DDD simplifiés dans un microservice](microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns.md)


### [Application des approches CQRS et CQS dans un microservice DDD dans eShopOnContainers](microservice-ddd-cqrs-patterns/eshoponcontainers-cqrs-ddd-microservice.md)


### [Implémentation de lectures/requêtes dans un microservice CQRS](microservice-ddd-cqrs-patterns/cqrs-microservice-reads.md)


### [Conception d’un microservice orienté DDD](microservice-ddd-cqrs-patterns/ddd-oriented-microservice.md)


### [Conception d’un modèle de domaine de microservice](microservice-ddd-cqrs-patterns/microservice-domain-model.md)


### [Implémentation d’un modèle de domaine de microservice avec .NET Core](microservice-ddd-cqrs-patterns/net-core-microservice-domain-model.md)


### [Seedwork (interfaces et classes de base réutilisables pour votre modèle de domaine)](microservice-ddd-cqrs-patterns/seedwork-domain-model-base-classes-interfaces.md)


### [Implémentation d’objets de valeur](microservice-ddd-cqrs-patterns/implement-value-objects.md)


### [Utilisation de classes d’énumération plutôt que de types enum](microservice-ddd-cqrs-patterns/enumeration-classes-over-enum-types.md)


### [Conception de validations dans la couche du modèle de domaine](microservice-ddd-cqrs-patterns/domain-model-layer-validations.md)


### [Validation côté client (validation dans les couches de présentation)](microservice-ddd-cqrs-patterns/client-side-validation.md)


### [Évènements de domaine : conception et implémentation](microservice-ddd-cqrs-patterns/domain-events-design-implementation.md)


### [Conception de la couche de persistance de l’infrastructure](microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-design.md)


### [Implémentation de la couche de persistance de l’infrastructure avec Entity Framework Core](microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-implemenation-entity-framework-core.md)


### [Utilisation de bases de données NoSQL comme infrastructure de persistance](microservice-ddd-cqrs-patterns/nosql-database-persistence-infrastructure.md)


### [Conception de la couche d’application et de l’API web de microservices](microservice-ddd-cqrs-patterns/microservice-application-layer-web-api-design.md)


### [Implémentation de la couche d’application de microservices à l’aide de l’API web](microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)


## [Implémentation d’applications résilientes](implement-resilient-applications/index.md)


### [Gestion d’une défaillance partielle](implement-resilient-applications/handle-partial-failure.md)


### [Stratégies pour la gestion d’une défaillance partielle](implement-resilient-applications/partial-failure-strategies.md)


### [Implémentation de nouvelles tentatives avec interruption exponentielle](implement-resilient-applications/implement-retries-exponential-backoff.md)


### [Implémentation de connexions SQL à Entity Framework Core résilientes](implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md)


### [Implémentation de nouvelles tentatives d’appel HTTP personnalisées avec interruption exponentielle](implement-resilient-applications/implement-custom-http-call-retries-exponential-backoff.md)


### [Implémentation de nouvelles tentatives d’appel HTTP avec interruption exponentielle avec Polly](implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md)


### [Implémentation du modèle de disjoncteur](implement-resilient-applications/implement-circuit-breaker-pattern.md)


### [Surveillance de l’intégrité](implement-resilient-applications/monitor-app-health.md)


## [Sécurisation des microservices .NET et des applications web](secure-net-microservices-web-applications/index.md)


### [À propos des autorisations dans les microservices .NET et les applications web](secure-net-microservices-web-applications/authorization-net-microservices-web-applications.md)


### [Stockage des secrets d’application en toute sécurité pendant le développement](secure-net-microservices-web-applications/developer-app-secrets-storage.md)


### [Utilisation d’Azure Key Vault pour protéger les secrets au moment de la production](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)


## [Points importants à retenir](key-takeaways.md)
