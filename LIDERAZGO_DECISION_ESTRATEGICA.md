# 🎯 DECISIONES ESTRATÉGICAS DEL PROYECTO

**Rama:** `leads-only` (Acceso restringido a Líderes)  
**Última actualización:** 31 de Octubre, 2025  
**Audiencia:** Solo Líderes del Proyecto  

---

## 📋 ÍNDICE

1. [Decisiones Clave Tomadas](#decisiones-clave-tomadas)
2. [Riesgos Identificados](#riesgos-identificados)
3. [Mitigación de Riesgos](#mitigación-de-riesgos)
4. [Recursos y Presupuesto](#recursos-y-presupuesto)
5. [Plan de Contingencia](#plan-de-contingencia)
6. [Comunicación Crítica](#comunicación-crítica)

---

## 🎯 DECISIONES CLAVE TOMADAS

### 1. **Arquitectura: Monolito vs Microservicios**

**Decisión:** Monolito (Backend único con Express/Node.js)

**Razón:**
- ✅ Equipo pequeño (10 personas)
- ✅ Proyecto 12 semanas (corto plazo)
- ✅ Complejidad manejable
- ✅ Fácil deployment inicial
- ❌ Microservicios = overhead innecesario ahora

**Alternativas descartadas:**
- Microservicios: Demasiado complejo para este timeline
- Serverless: Datos sensibles requieren control

**Decisión válida por:** 12 meses. Si crece, re-evaluar.

---

### 2. **Base de Datos: MongoDB**

**Decisión:** MongoDB (NoSQL)

**Razón:**
- ✅ Flexible para datos clínicos variables
- ✅ Escalable horizontalmente
- ✅ JSON-like (React/JS friendly)
- ✅ Gratis en Atlas para desarrollo
- ✅ Comunidad grande

**Alternativa:** PostgreSQL
- Más seguro para datos críticos
- Pero requiere schema rígido

**Decisión:** MongoDB por velocidad, reevaluar después de Fase 1 si datos requieren SQL

---

### 3. **Frontend: React + Vite**

**Decisión:** React 18 + Vite + TypeScript + PWA

**Razón:**
- ✅ React domina mercado (fácil contratar)
- ✅ Vite = compilación rápida (DX)
- ✅ TypeScript = menos bugs
- ✅ PWA = funciona offline (hospital)
- ✅ Material-UI = componentes ya hechos

**Alternativa:** Vue/Angular/Svelte
- Son válidos pero React es más conocido

**Decisión:** React. No es optimal, es pragmático.

---

### 4. **Autenticación: JWT + Refresh Tokens**

**Decisión:** JWT con Refresh Tokens + HttpOnly Cookies

**Razón:**
- ✅ Seguro
- ✅ Escalable
- ✅ Sin sesiones en servidor
- ✅ Estándar industrial

**Alternativa:** OAuth/SAML
- Overkill para MVP
- Implementar después

**Decisión:** JWT ahora, OAuth después si hospital lo requiere

---

### 5. **Deployment: Docker + Cloud (AWS/Azure/DigitalOcean)**

**Decisión:** Docker Compose local, Cloud Staging después

**Razón:**
- ✅ Reproducible
- ✅ Fácil escalabilidad
- ✅ Listo para CI/CD

**Timing:**
- Semana 0-6: Local + Staging en cloud (demo)
- Semana 7-8: Testing en cloud
- Semana 9-12: Piloto en hospital

**Presupuesto:** ~$50-200/mes en cloud (re-evaluar)

---

## ⚠️ RIESGOS IDENTIFICADOS

### 🔴 CRÍTICOS

#### Risk 1: Datos Sensibles + Seguridad
```
Probabilidad: Alta
Impacto: Crítico (legal, médico)
Descripción: Datos de pacientes comprometidos

Síntomas de alerta:
- SQL injection, XSS, insecure storage
- Acceso no autorizado
- Encriptación débil

Prevención:
- Code review obligatorio
- OWASP Top 10 en checklist
- Penetration testing semana 8
- HIPAA/datos sensibles = prioridad
```

#### Risk 2: Timeline Ajustado (12 semanas)
```
Probabilidad: Alta
Impacto: Alto (retraso en piloto)
Descripción: No terminar a tiempo

Síntomas de alerta:
- Backend atrasado en Semana 3
- Frontend no integrado Semana 4
- Hospital pide cambios mayores Semana 5

Prevención:
- Daily standups obligatorios
- Sprint planning riguroso
- MVP claro (no "nice to have")
- Cortes de features si es necesario
```

#### Risk 3: Hospital Requiere Cambios Mayores
```
Probabilidad: Media-Alta
Impacto: Crítico
Descripción: Hospital dice "esto no funciona" Semana 8

Síntomas de alerta:
- Pocos requisitos en Semana 1-2
- Hospital no responde feedback rápido
- Cambios de scope frecuentes

Prevención:
- Reuniones con hospital cada 3 días
- Validación de wireframes Semana 2
- MVP claro ANTES de código
- Comunicación asincrónica documentada
```

### 🟡 ALTOS

#### Risk 4: Equipo Desalineado
```
Probabilidad: Media
Impacto: Alto (producto inconsistente)
Descripción: Frontend y backend usan diferentes estándares

Síntomas de alerta:
- PRs rechazadas frecuentemente
- Conflictos en arquitectura
- Comunicación en Slack caótica

Prevención:
- ADRs (Architecture Decision Records)
- Code review checklist
- Standup enfocado en blockers
- Documentación compartida en Wiki
```

#### Risk 5: Pérdida de Miembro Clave
```
Probabilidad: Baja
Impacto: Alto
Descripción: Backend Lead se va Semana 5

Síntomas de alerta:
- Poco conocimiento transferido
- Documentación inexistente
- Silos de conocimiento

Prevención:
- Pair programming semanal
- Documentación de decisiones
- Onboarding de backup
- Conocimiento compartido
```

### 🟢 MEDIOS

#### Risk 6: Tecnología Desconocida
```
Probabilidad: Baja
Impacto: Medio
Descripción: Alguien del equipo no conoce Vite/TypeScript

Síntomas de alerta:
- Preguntas básicas frecuentes
- Progreso lento
- Frustración del dev

Prevención:
- Setup.md paso a paso
- Video tutorials preparados
- Pair programming primeras 2 semanas
- Slack #help channel
```

---

## 🛡️ MITIGACIÓN DE RIESGOS

### Por Fase

#### **Fase 0: Setup (Semana 0)**
```
Risk 1 (Seguridad):
├─ Crear security checklist
├─ Designar Security Lead
└─ Training sobre OWASP

Risk 2 (Timeline):
├─ MVP bien definido (documento)
├─ Roadmap realista
└─ Buffer 15% en timeline

Risk 3 (Hospital):
├─ Kickoff meeting larga
├─ Whiteboard sesión con hospital
├─ Requisitos en Confluence
└─ Sign-off antes de código
```

#### **Fase 1: Requisitos (Semana 1-2)**
```
Risk 3 (Hospital):
├─ 3 reuniones con hospital
├─ Prototipo paper UI
├─ Validación de flujos
└─ Documento de requisitos signed

Risk 4 (Desalineación):
├─ Arquitectura tech design review
├─ API spec en Swagger
├─ DB schema review
└─ ADRs para decisiones
```

#### **Fase 2: Desarrollo (Semana 3-6)**
```
Risk 1 (Seguridad):
├─ Security review en cada PR
├─ Static security scan (SonarQube)
├─ Dependency scanning (npm audit)
└─ OWASP checklist diario

Risk 2 (Timeline):
├─ Burndown chart público
├─ Daily standup 15 min
├─ Feature freeze Semana 5
└─ Sprint velocity tracking

Risk 5 (Pérdida de miembro):
├─ Documentación de decisiones
├─ ADRs todos los días
├─ Pair programming 20% tiempo
└─ Backup person por rol
```

#### **Fase 3: Validación (Semana 7-8)**
```
Risk 1 (Seguridad):
├─ Penetration testing
├─ Security audit completo
├─ Remediación
└─ Retest

Risk 3 (Hospital feedback):
├─ UAT con hospital
├─ Feedback incorporado
├─ Re-testing
└─ Sign-off para piloto
```

#### **Fase 4: Piloto (Semana 9-12)**
```
Risk 1 (Seguridad):
├─ Monitoring 24/7
├─ Audit logs completos
├─ Incident response plan
└─ On-call rotation

Risk 6 (Problemas técnicos):
├─ Hotfix procedure
├─ Rollback procedure
├─ Communication plan
└─ Status page
```

---

## 💰 RECURSOS Y PRESUPUESTO

### Equipo (10 personas)

```
BACKEND (5)
├─ Lead: $150-200 USD/día (full time)
├─ Senior Dev (2): $120-150 USD/día c/u
├─ Mid Dev: $90-120 USD/día
└─ Junior Dev: $50-80 USD/día

FRONTEND (4)
├─ Lead: $150-200 USD/día
├─ Senior Dev (1): $120-150 USD/día
├─ Mid Dev: $90-120 USD/día
└─ Junior Dev: $50-80 USD/día

DEVOPS/QA (1)
└─ Engineer: $120-150 USD/día

LIDERAZGO (Ya incluido en leads)
```

**Total 12 semanas:** ~$150,000 - $200,000 USD (estimado bruto)

---

### Infraestructura

```
Desarrollo (Codespaces/Local):
├─ GitHub Codespaces: $0 (incluido)
├─ Gratis para estudiantes
└─ Licencias: $0 (open source tools)

Staging:
├─ AWS EC2 t3.small: ~$30/mes
├─ RDS MongoDB Atlas: ~$0 (free tier)
└─ Total: ~$30-50/mes

Monitoreo:
├─ Sentry (errors): $29/mes
├─ New Relic (APM): $0 (free tier)
├─ CloudWatch (logs): ~$10/mes
└─ Total: ~$40/mes

Networking:
├─ Dominio: $10-15/año
├─ SSL: $0 (Let's Encrypt)
└─ Total: ~$1/mes

TOTAL INFRAESTRUCTURA: ~$70-100/mes
```

---

### Softwares y Servicios

```
Essencial:
├─ GitHub Pro: $4/persona/mes (~$40)
├─ Slack: $0 (free tier)
├─ Notion: $0 (free tier)
└─ Total: ~$40/mes

Recomendado:
├─ Figma (diseño): $12/mes
├─ GitKraken (Git): $0 (free)
├─ SonarQube (security): $0 (open source)
├─ Postman (API): $0 (free)
└─ Total: ~$12/mes

TOTAL SERVICIOS: ~$52/mes
```

**PRESUPUESTO TOTAL 12 SEMANAS:**
- Equipo: $150k-200k
- Infraestructura: ~$0.8k
- Servicios: ~$0.6k
- **TOTAL: ~$151k-201k USD**

---

## 🚨 PLAN DE CONTINGENCIA

### Escenario 1: Backend Atrasado (Semana 4)

```
Síntomas:
├─ API endpoints <50% completados
├─ Database schema incomplete
└─ Tests fallando

Acciones inmediatas:
├─ War room con backend lead
├─ Priorizar endpoints críticos
├─ Frontend usa mocks mientras tanto
├─ Extends sprint si es necesario
└─ Evalúa reducir scope

Timeline afectado:
└─ +1 semana posible
```

### Escenario 2: Hospital Requiere Cambios Mayores (Semana 6)

```
Síntomas:
├─ "El sistema no funciona como esperamos"
├─ Cambios en flujo principal
└─ Retrasos significativos

Acciones inmediatas:
├─ Reunión urgente con hospital + leads
├─ Categorizar: crítico vs nice-to-have
├─ Crear nuevo sprint con cambios
├─ Comunica timeline revisado a equipo
└─ Ajusta presupuesto si es necesario

Timeline afectado:
└─ +1-2 semanas posible
```

### Escenario 3: Miembro Crítico se Va (Semana 5)

```
Síntomas:
├─ Aviso de renuncia
├─ Conocimiento concentrado
└─ Proyecto en riesgo

Acciones inmediatas:
├─ Transferencia urgente (1 semana)
├─ Designa backup immediately
├─ Pair programming intenso
├─ Documentación acelerada
└─ Redistribución de tareas

Timeline afectado:
└─ +2 semanas posible

Prevención ya en lugar:
└─ Backup person asignado Semana 0
```

### Escenario 4: Problema de Seguridad Crítico (Semana 8)

```
Síntomas:
├─ Vulnerabilidad SQL injection
├─ XSS vulnerability
├─ Acceso no autorizado
└─ Data breach

Acciones inmediatas:
├─ Pause todo (feature freeze)
├─ War room de seguridad
├─ Identificar scope del problema
├─ Parche y deploy
├─ Auditoría de código
└─ Post-mortem

Timeline afectado:
└─ +1 semana, pero crítico

Prevención:
└─ Security reviews obligatorios
```

### Escenario 5: Hospital No Participa en UAT (Semana 7)

```
Síntomas:
├─ Hospital no responde
├─ Sin acceso a usuarios reales
├─ No puedes validar sistema
└─ Incertidumbre de piloto

Acciones inmediatas:
├─ Contacta directamente a hospital
├─ Escalate si es necesario
├─ Crea demo interna como "UAT"
├─ Plan B: piloto solo con IT hospital
└─ Contingencia: delay de piloto

Timeline afectado:
└─ +1-2 semanas posible
```

---

## 💬 COMUNICACIÓN CRÍTICA

### Escalation Matrix

```
PROBLEMA                    QUIÉN CONTACTAR      TIMELINE
────────────────────────────────────────────────────────────
Backend 2+ semanas atrás    Backend Lead        24 horas
Frontend bloqueado          Frontend Lead       12 horas
Hospital requiere cambios   Tú + Co-líder       24 horas
Problema seguridad          Security Lead       4 horas
Miembro quiere renunciar    Tú solo             2 horas
Presupuesto comprometido    Tú solo             24 horas
Incidente en producción     Tú + DevOps         1 hora
```

### Reuniones Críticas

```
REUNIÓN                     FRECUENCIA    AUDIENCIA              DURACIÓN
─────────────────────────────────────────────────────────────────────────
Daily Standup              Diario        Todos                  15 min
Leads Sync                 3x/semana     Tú + Co-líder + Leads  30 min
Sprint Planning            Viernes       Todos                  1 hora
Hospital Sync              2x/semana     Tú + Hospital + lead   45 min
Retrospective              Viernes       Todos                  30 min
Security Review            2x/semana     Security + devs        1 hora
Emergency War Room         As needed     Leads + especialista   variable
```

### Documentación Crítica

```
Documento                          Responsable    Actualización
──────────────────────────────────────────────────────────────
ADRs (Decisiones técnicas)        Tech Lead      Cuando hay decisión
Requisitos Hospital               Tú             Después cada meeting
Riesgos y mitigación              Tú             Semana 0, 4, 8
Timeline y burndown               Scrum Master   Diario
Security checklist                Security Lead  Diario
Incidentes y post-mortems         Tú             Cuando hay incidente
```

---

## 📊 MÉTRICAS DE ÉXITO

### Técnicas

```
Métrica                      Target          Frecuencia Medición
──────────────────────────────────────────────────────────────────
Code Coverage                >80%            Semanal
Security vulnerabilities     0 críticos      Diario
Deployment frequency         1x/semana       Semanal
MTTR (Mean Time To Repair)   <2 horas        Cuando hay incidente
API Response time            <200ms          Diario
Uptime                       >99%            Mensual
```

### Equipo

```
Métrica                      Target          Frecuencia Medición
──────────────────────────────────────────────────────────────────
Sprint velocity              Consistente     Semanal
PR review time               <24 horas       Semanal
Code quality (linting)       100% pass       Diario
Test pass rate               100%            Diario
Deployment success           >95%            Semanal
Team satisfaction            >7/10           Mensual
```

### Negocio

```
Métrica                      Target          Frecuencia Medición
──────────────────────────────────────────────────────────────────
Timeline adherence           100% (12 sem)   Semanal
Budget adherence             100%            Mensual
Hospital satisfaction        >8/10           Después UAT
Feature completion           100% MVP        Semana 6
UAT pass rate                >95%            Semana 8
Piloto ready                 Go/No-go        Semana 9
```

---

## 🔐 DECISIONES CONFIDENCIALES

### Por Decidir (Requiere Discusión Líderes)

```
1. Proveedor de Cloud
   - AWS vs Azure vs DigitalOcean?
   - Implicaciones de costo
   - Soporte local?

2. Compensación del equipo
   - Bono por on-time delivery?
   - Bono por cero vulnerabilidades?

3. Escalabilidad post-MVP
   - ¿Microservicios después?
   - ¿Otra geografía?

4. Venta/Licencia del software
   - ¿Vender a otros hospitales?
   - ¿Modelo de negocio?
   - ¿Open source después?
```

---

## ✅ APROBACIONES REQUERIDAS

- [ ] Tech Lead: Decisiones técnicas
- [ ] Hospital: Requisitos y timeline
- [ ] Finanzas: Presupuesto
- [ ] Liderazgo: Riesgos y contingencias
- [ ] Legal: Datos sensibles y cumplimiento

---

## 📞 CONTACTO

**Preguntas sobre:**
- **Decisiones estratégicas** → Tú
- **Riesgos técnicos** → Tech Lead
- **Hospital reqs** → Project Manager
- **Presupuesto** → Finance
- **Seguridad** → Security Lead

---

**Última actualización:** 31 de Octubre, 2025  
**Rama:** `leads-only` (Acceso restringido)  
**Estado:** Activo - Revisar cada 2 semanas
