# RAG Self-Correction con LangGraph

## Overview
Este repositorio implementa un sistema de Retrieval-Augmented Generation (RAG) agéntico diseñado para minimizar alucinaciones en entornos de producción. A diferencia de los flujos lineales, esta arquitectura utiliza un grafo de estados para validar la relevancia de la información recuperada y la precisión de la respuesta antes de su entrega.

## Core Architecture
El sistema utiliza LangGraph para orquestar un flujo de trabajo cíclico:

Retrieval Node: Búsqueda semántica en base de datos vectorial (FAISS).

Validation Node: Evaluación mediante un modelo "LLM-as-a-Judge" para calificar la relevancia del contexto.

Self-Correction: Si la información es insuficiente, el agente redefine la estrategia de búsqueda y re-intenta la recuperación.

Generation & Hallucination Check: Síntesis final de la respuesta basada estrictamente en los documentos validados.

## Tech Stack
Framework: LangChain & LangGraph

LLM: OpenAI (GPT-4o / GPT-4-turbo)

Vector Store: FAISS

Language: Python 3.10+

## Quick Start
Instalación:

Bash
pip install -r requirements.txt
Configuración:
Crea un archivo .env con tu OPENAI_API_KEY.

Ejecución:
Ejecuta el notebook para inicializar el grafo y procesar consultas con validación automática.
