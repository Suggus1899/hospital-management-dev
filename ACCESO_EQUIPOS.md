# 🔐 CONTROL DE ACCESO Y ROLES DEL EQUIPO

**Rama:** `leads-only` (Acceso restringido a Líderes)  
**Propósito:** Documentar niveles de acceso y permisos del equipo  
**Acceso:** Solo Tú + Co-líder  
**Última actualización:** 31 de Octubre, 2025  

---

## 📑 ÍNDICE

- [Matriz de Acceso GitHub](#matriz-de-acceso-github)
- [Permisos por Rol](#permisos-por-rol)
- [Datos Confidenciales](#datos-confidenciales)
- [Proceso de Onboarding](#proceso-de-onboarding)
- [Auditoría de Acceso](#auditoría-de-acceso)

---

## 🔑 MATRIZ DE ACCESO GITHUB

### Estructura de Ramas

```
main (Producción)
├─ Acceso: Tú + Co-líder (push, merge)
├─ Protección: ✅ Requiere 2 reviews
├─ Contenido: Código estable, deployable
└─ CI/CD: ✅ Automático a producción

develop (Integración)
├─ Acceso: Tech leads (push, merge)
├─ Protección: ✅ Requiere 1 review
├─ Contenido: Código integrado, testeable
└─ CI/CD: ✅ Deploy a staging

feature/* (Desarrollo)
├─ Acceso: Todos (create, push)
├─ Protección: ❌ Sin restricción
├─ Contenido: Work in progress
└─ Política: Auto-delete después de merge

leads-only (Liderazgo)
├─ Acceso: Tú + Co-líder (push, merge)
├─ Protección: ✅ Requiere admin approval
├─ Contenido: Decisiones estratégicas, riesgos, actas
└─ Visibilidad: No aparece en GitHub board público
```

### Tabla de Acceso

| Persona | GitHub Role | main | develop | feature/* | leads-only | Descripción |
|---------|-----------|------|---------|-----------|-----------|-------------|
| Tú | Admin | ✅ | ✅ | ✅ | ✅ | Líder principal |
| Co-líder | Admin | ✅ | ✅ | ✅ | ✅ | Líder técnico |
| Dev 1 (Backend Lead) | Write | ❌ | ✅ | ✅ | ❌ | Responsable backend |
| Dev 2 (Frontend Lead) | Write | ❌ | ✅ | ✅ | ❌ | Responsable frontend |
| Dev 3-8 (Backend) | Write | ❌ | ✅ | ✅ | ❌ | Equipo backend |
| Dev 9-10 (Frontend) | Write | ❌ | ✅ | ✅ | ❌ | Equipo frontend |
| Hospital Stakeholder* | Read | ✅ | ❌ | ❌ | ❌ | Opcional, solo lectura |
| DevOps (si existe) | Admin | ✅ | ✅ | ✅ | ❌ | Deploy y infraestructura |

*El stakeholder del hospital NO debe invitarse al repositorio privado. Usar wiki/docs públicas en su lugar.

---

## 👥 PERMISOS POR ROL

### ADMIN (Admins del Proyecto)

**Quién:** Tú + Co-líder

```
Permisos
├─ ✅ Push a cualquier rama
├─ ✅ Crear y eliminar ramas
├─ ✅ Mergear sin reviews
├─ ✅ Configurar protecciones de ramas
├─ ✅ Acceso a secrets y variables
├─ ✅ Configurar CI/CD
├─ ✅ Acceso a leads-only
├─ ✅ Invitar/remover usuarios
└─ ✅ Acceso a settings del repo

Responsabilidades
├─ Decisiones finales de arquitectura
├─ Aprobación de merges a main
├─ Escalation de problemas críticos
├─ Gestión de releases
├─ Cumplimiento de security
└─ Performance del equipo
```

### WRITE (Tech Leads + Devs)

**Quién:** Todos los desarrolladores (8 personas)

```
Permisos
├─ ✅ Push a develop y feature/*
├─ ❌ Mergear a main
├─ ❌ Eliminar ramas
├─ ✅ Crear pull requests
├─ ✅ Revisar código (comentarios)
├─ ❌ Acceso a secrets
└─ ✅ Ver GitHub Actions

Responsabilidades
├─ Escribir código de calidad
├─ Revisar PRs de compañeros
├─ Reportar bugs y riesgos
├─ Cumplir con estándares de código
├─ Documentar cambios
└─ Participar en retrospectives
```

### READ (Stakeholders - Opcional)

**Quién:** Hospital stakeholder (si aplica)

```
Permisos
├─ ✅ Clonar repositorio
├─ ✅ Ver código en main
├─ ✅ Ver GitHub Issues
├─ ❌ Crear ramas
├─ ❌ Push
├─ ❌ Mergear
└─ ❌ Ver GitHub Actions

Responsabilidades
├─ Revisar código cuando se solicite
├─ Proporcionar feedback
└─ Validar requisitos en main
```

---

## 🔒 DATOS CONFIDENCIALES

### Acceso Restringido a Tú + Co-líder

#### En GitHub (Secrets)

```
HOSPITAL_API_KEY
PAYMENT_GATEWAY_SECRET
JWT_PRIVATE_KEY
DATABASE_PASSWORD
SMTP_PASSWORD
AWS_SECRET_ACCESS_KEY
```

**Gestión:**
- ✅ Usar GitHub Secrets para CI/CD
- ✅ Nunca pushear a repositorio
- ✅ Rotar cada 3 meses
- ✅ Auditar acceso mensualmente

#### En Rama leads-only

```
Documentos privados
├─ LIDERAZGO_DECISION_ESTRATEGICA.md (Decisiones clave)
├─ RIESGOS_CRITICOS.md (Riesgos identificados)
├─ ACTAS_REUNIONES_LIDERES.md (Actas privadas)
└─ PRESUPUESTO_DETALLADO.md (Costos sensibles)
```

**Acceso:**
- ✅ Solo push de admins
- ✅ Requiere 2 revisiones antes de merge
- ✅ Histórico de commits auditado
- ✅ Nunca mergear a main o develop

#### En Workspace Privado

```
Información fuera del repo
├─ Salarios y compensación
├─ Evaluaciones personales
├─ Negociaciones con hospital
├─ Decisiones de inversión
└─ Planes post-proyecto
```

**Gestión:**
- ✅ Google Drive privado (compartido solo con co-líder)
- ✅ Documentos cifrados
- ✅ Acceso limitado
- ✅ Auditoría de downloads

---

## 🎯 PROCESO DE ONBOARDING

### Semana 0: Preparación

**Tarea:** Tú + Co-líder

```
Checklist
├─ [ ] Crear cuentas GitHub para todos (si no existen)
├─ [ ] Preparar lista de emails
├─ [ ] Preparar presentación del proyecto
└─ [ ] Crear canal Slack #hospital-management
```

### Semana 1: Acceso al Repositorio

**Tarea:** Co-líder (invitar usuarios)

```
Para cada desarrollador:
├─ [ ] Enviar invitación GitHub
├─ [ ] Especificar role (Admin o Write)
├─ [ ] Compartir CONTRIBUTING.md
├─ [ ] Compartir SETUP_INICIAL.md
└─ [ ] Confirmar acceso funcionando

Control:
├─ [ ] Documentar fecha de invitación
├─ [ ] Archivar email de confirmación
└─ [ ] Verificar en GitHub que aparece
```

### Semana 1-2: Onboarding Técnico

**Tarea:** Tech leads

```
Para cada desarrollador:
├─ [ ] 1-to-1 de 30 minutos
├─ [ ] Explicar flujo de ramas
├─ [ ] Setup local (backend + frontend)
├─ [ ] Crear primer PR
├─ [ ] Code review de primer PR
└─ [ ] Merge a develop

Documento: Compartir SETUP_INICIAL.md
```

### Semana 2-3: Onboarding de Requisitos

**Tarea:** Tú

```
Para todo el equipo:
├─ [ ] Presentación de hospital (context)
├─ [ ] Explicar requisitos de pacientes
├─ [ ] Explicar requisitos de citas
├─ [ ] Explicar requisitos de reportes
├─ [ ] Q&A session
└─ [ ] Documentar preguntas frecuentes
```

### Semana 3: Sprint Planning

**Tarea:** Todos

```
├─ [ ] Revisar backlog inicial
├─ [ ] Estimar tickets
├─ [ ] Asignar trabajo
├─ [ ] Comenzar Sprint 1
└─ [ ] Daily standup (Slack)
```

---

## 🔍 AUDITORÍA DE ACCESO

### Mensual: Revisión de Accesos

**Fecha:** Último viernes de mes

```sql
-- Verificar quién tiene acceso
SELECT * FROM github.collaborators 
WHERE repo = 'hospital-management-system'
ORDER BY created_at DESC;

-- Verificar cambios recientes
SELECT * FROM github.audit_log 
WHERE repo = 'hospital-management-system'
AND created_at > DATE_SUB(NOW(), INTERVAL 30 DAY)
AND action LIKE 'member.%';
```

**Checklist de Auditoría:**

| Item | Estado | Fecha | Notas |
|------|--------|-------|-------|
| Revisar colaboradores activos | ✅ | | |
| Verificar permisos correctos | ✅ | | |
| Remover acceso inactivos | ✅ | | |
| Rotar secrets (q3m) | ✅ | | |
| Revisar GitHub Actions | ✅ | | |
| Revisar branch protection | ✅ | | |

### Cuando Alguien Se Va

**Immediato (mismo día):**

```
├─ [ ] Remover acceso GitHub
├─ [ ] Revocar secrets
├─ [ ] Cambiar passwords compartidos
├─ [ ] Comunicar a equipo
└─ [ ] Audit log
```

**En 24 horas:**

```
├─ [ ] Reasignar tareas en progreso
├─ [ ] Revisión de commits
├─ [ ] Documentar handover
└─ [ ] Archivar emails
```

**Documentación:**

```
Crear documento para registro:
├─ Nombre
├─ Fecha de salida
├─ Último commit
├─ Tareas pendientes
└─ Razón de salida (interno)
```

---

## 📋 INVENTARIO DE ACCESOS

### Actual (31 Oct 2025)

```
Admins (2)
├─ [Tu nombre]
└─ [Co-líder nombre]

Write Access (8)
├─ Dev 1: [Backend Lead]
├─ Dev 2: [Frontend Lead]
├─ Dev 3: [Backend]
├─ Dev 4: [Backend]
├─ Dev 5: [Backend]
├─ Dev 6: [Frontend]
├─ Dev 7: [Frontend]
└─ Dev 8: [Frontend]

Read Access (0)
└─ (Vacío - stakeholders en wiki externa)
```

### Cambios Previstos

```
Mes 1: ✅ Completo
Mes 2: ¿Posible DevOps? → Admin
Mes 3: ¿Posible QA? → Write
Post-MVP: ¿Open source? → Read para comunidad
```

---

## 🔐 PROTECCIONES DE RAMA

### main

```
✅ Require pull request reviews: 2 approvals
✅ Require status checks: ESLint + Tests + Build
✅ Require branches to be up to date
✅ Include administrators: NO (admins pueden bypassar)
✅ Allow auto-merge: NO
✅ Allow deletions: NO
```

### develop

```
✅ Require pull request reviews: 1 approval (tech lead)
✅ Require status checks: ESLint + Tests
✅ Require branches to be up to date: SI
✅ Include administrators: NO
✅ Allow auto-merge: SI (después de aprobación)
✅ Allow deletions: NO
```

### leads-only

```
✅ Require pull request reviews: 1 approval (admin)
✅ Require status checks: NONE
✅ Require branches to be up to date: SI
✅ Include administrators: SI (solo admins pueden)
✅ Allow auto-merge: NO
✅ Allow deletions: NO
```

---

## 📞 CONTACTOS Y ESCALATION

### Problemas de Acceso

```
Problema: Dev no puede hacer push
├─ Paso 1: Verificar permisos en GitHub
├─ Paso 2: Verificar SSH key configurada
├─ Paso 3: Contactar co-líder
└─ Tiempo esperado: < 1 hora

Problema: Dev necesita acceso a leads-only
├─ Contactar: Tú (líder principal)
├─ Razón: Solo admins tienen acceso
├─ Aprobación: Manual del líder
└─ Tiempo esperado: < 24 horas
```

---

**Rama:** `leads-only` (Acceso restringido)  
**Documento activo:** Sí  
**Próxima revisión:** 30 Nov 2025
