webnovel_recommender/
│
├── .env                          # Stores secrets and environment variables. DO NOT commit to Git.
├── README.md                     # Project overview, setup, and execution instructions.
├── requirements.txt              # A list of Python packages needed for the project.
├── generate_index.py             # A one-off utility script to pre-compute the FAISS index.
├── main.py                       # The application's main entry point. Initializes and assembles everything.
│
├── data/
│   └── webnovels.csv             # Raw input data for the recommendation engine.
│
├── saved_models/
│   └── webnovel_index.faiss      # The pre-computed, optimized FAISS index file for fast searches.
│
├── notebooks/
│   └── experimentation.ipynb     # Jupyter notebooks for data analysis and model prototyping.
│
├── src/
│   ├── __init__.py               # Makes 'src' a Python package.
│   │
│   ├── config/
│   │   ├── __init__.py
│   │   └── settings.py           # Loads and holds all application settings and configurations from .env.
│   │
│   ├── recommendations/          # FEATURE MODULE 1: Handles all recommendation-related logic.
│   │   ├── __init__.py
│   │   ├── api/                  # Handles web communication for this feature.
│   │   │   ├── __init__.py
│   │   │   ├── routes.py         # Defines API endpoints (e.g., GET /recommendations). The "Controller" layer.
│   │   │   └── schemas.py        # Pydantic models for API request/response validation. Data Transfer Objects (DTOs).
│   │   ├── services/             # Contains the core business logic for this feature.
│   │   │   ├── __init__.py
│   │   │   └── main_service.py   # Orchestrates the steps to generate recommendations. The "Service" layer.
│   │   └── domain/               # Defines the core business entities for this feature.
│   │       ├── __init__.py
│   │       └── webnovel.py       # Pydantic model representing the Webnovel business entity.
│   │
│   ├── reviews/                  # FEATURE MODULE 2: Example of how a future feature would be structured.
│   │   ├── __init__.py
│   │   ├── api/
│   │   ├── services/
│   │   └── domain/
│   │
│   └── shared/                   # SHARED KERNEL: Code that can be used by any feature.
│       ├── __init__.py
│       ├── infrastructure/       # Code that connects to external systems (DBs, models, APIs).
│       │   ├── __init__.py
│       │   ├── clients.py        # Clients to connect to FAISS, SentenceTransformer models, databases, etc.
│       │   └── logging.py        # Centralized logging configuration for the entire application.
│       └── utils/                # Generic, reusable helper functions.
│           ├── __init__.py
│           └── text_utils.py     # Helper functions for text cleaning, normalization, etc.
│
├── tests/                        # Contains all automated tests for the application.
│   ├── __init__.py
│   └── recommendations/          # Test structure mirrors the 'src' structure.
│       └── test_recommendation_service.py # Unit/Integration tests for the recommendation service.
│
└── .gitignore                    # Specifies which files and folders Git should ignore.
