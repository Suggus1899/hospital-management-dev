# 📋 ACTAS DE REUNIONES LÍDERES

**Rama:** `leads-only` (Acceso restringido a Líderes)  
**Propósito:** Registro de decisiones y discusiones privadas  
**Acceso:** Solo Tú + Co-líder  

---

## 📑 ÍNDICE

- [Reunión Kickoff Líderes](#reunión-kickoff-líderes)
- [Reunión Pre-Proyecto](#reunión-pre-proyecto)
- [Template para Futuras Reuniones](#template-para-futuras-reuniones)

---

## 🎯 REUNIÓN KICKOFF LÍDERES

**Fecha:** 31 de Octubre, 2025  
**Asistentes:** Tú + Co-líder  
**Duración:** 1.5 horas  
**Lugar:** Virtual / En persona  

### Agenda Completada

✅ Visión del proyecto  
✅ Equipos y asignaciones  
✅ Timeline y hitos críticos  
✅ Riesgos identificados  
✅ Comunicación y escalation  
✅ Próximos pasos  

### Decisiones Tomadas

#### 1. Estructura de Liderazgo
```
Tú:
├─ Líder principal
├─ Decisiones finales
├─ Hospital relationship
└─ Punto de escalation

Co-líder:
├─ Líder técnico (o segundo en cargo)
├─ Tech decisions
└─ Daily standups
```

#### 2. Comunicación Interna (Líderes)

```
Canal: Slack privado #leads-only
Frecuencia:
├─ Mensajes ad-hoc (urgencias)
├─ Sync 3x/semana (30 min)
└─ Meeting mensual (1 hora)

Temas:
├─ Decisions críticas
├─ Riesgos y mitigación
├─ Feedback del equipo
├─ Hospital relationships
└─ Personal challenges
```

#### 3. Comunicación con Equipo

```
Pública (Todo el equipo ve):
├─ Daily standup (Slack)
├─ Sprint planning (Viernes)
├─ Retrospective (Viernes)
└─ Roadmap (GitHub)

Privada (Leads solo):
├─ Decisiones estratégicas
├─ Performance feedback
├─ Problemas sensibles
└─ Cambios de scope
```

#### 4. Decisiones sobre Alcance

**MVP Definitivo:**
```
Backend:
├─ Authentication (JWT)
├─ Patient CRUD
├─ Appointments CRUD
├─ Doctor Dashboard
└─ Basic reports

Frontend:
├─ Login
├─ Patient management
├─ Appointment booking
├─ Reports view
└─ Responsive design

NO incluido en MVP:
├─ Billing system
├─ Advanced analytics
├─ Multi-language
├─ Mobile app (PWA es suficiente)
└─ AI features
```

**Decisión:** MVP es MVP. No "nice to have". Feature freeze Semana 5.

#### 5. Resolución de Conflictos

```
Escala:
1. Devs resuelven entre sí (24 horas)
2. Escalate a tech lead (24 horas)
3. Escalate a ustedes (48 horas)
4. Nosotros decidimos (final)

Principio:
└─ Oír a ambas partes, decidir rápido
```

#### 6. Performance del Equipo

```
Medición:
├─ Sprint velocity
├─ Code quality (linting)
├─ Test coverage
├─ Deployment success
└─ Team happiness

Si alguien atrasa:
├─ 1 semana: Chat privado
├─ 2 semanas: Plan de mejora
├─ 3 semanas: Re-evaluación de rol
└─ 4 semanas: Cambio de rol o salida
```

#### 7. Escalation para Hospital

```
Situaciones que requieren escalation:
├─ Cambios de requisitos mayores
├─ Delays significativos
├─ Problemas de seguridad
├─ Presupuesto comprometido
└─ Timeline en riesgo

Protocolo:
├─ Identificar problema (24 horas)
├─ Crear plan de mitigación (24 horas)
├─ Comunicar a hospital (48 horas)
└─ Update semanales hasta resolución
```

### Action Items

| Item | Responsable | Fecha | Status |
|------|------------|-------|--------|
| Kickoff con equipo | Tú | 3-4 Nov | ⏳ Pending |
| Contactar hospital coordinador | Tú | 1-2 Nov | ⏳ Pending |
| Crear Slack #leads-only | Co-líder | 1 Nov | ⏳ Pending |
| Crear canal #security | Co-líder | 1 Nov | ⏳ Pending |
| Preparar presentación proyecto | Tú + Co-líder | 2 Nov | ⏳ Pending |
| Proteger rama leads-only en GitHub | Co-líder | 1 Nov | ✅ Done |

---

## 📞 REUNIÓN PRE-PROYECTO

**Fecha:** (A programar)  
**Asistentes:** Tú + Co-líder + Hospital Contact  
**Duración:** 2 horas  
**Propósito:** Validar requisitos antes de código  

### Checklist

```
Requisitos Funcionales
├─ [ ] Flujos de pacientes documentados
├─ [ ] Flujos de citas documentados
├─ [ ] Flujos de reportes documentados
├─ [ ] Integraciones con sistemas existing
├─ [ ] Reportes requeridos mapeados
└─ [ ] Usuarios y roles claros

Requisitos No-Funcionales
├─ [ ] Performance requirements (usuarios simultáneos)
├─ [ ] Disponibilidad (uptime required)
├─ [ ] Cumplimiento (HIPAA/GDPR/local)
├─ [ ] Integración con hospitales existentes
└─ [ ] Backup y disaster recovery

Infraestructura Hospital
├─ [ ] Internet bandwidth
├─ [ ] Servidores disponibles
├─ [ ] IT team support
├─ [ ] Security requirements
└─ [ ] Timeline hospital
```

---

## 📋 TEMPLATE PARA FUTURAS REUNIONES

### [REUNIÓN] - Fecha

**Asistentes:**  
**Duración:**  
**Lugar:**  

### Agenda

- [ ] Item 1
- [ ] Item 2
- [ ] Item 3

### Discusión

**Item 1:** [Detalle]
```
Decisión:
Responsable:
Deadline:
```

### Decisiones

| Decisión | Responsable | Deadline | Status |
|----------|------------|----------|--------|
| X | Y | Fecha | Status |

### Action Items

| Item | Responsable | Fecha |
|------|------------|-------|
| X | Y | Fecha |

### Notas Adicionales

```
(Espacio para notas privadas no estructuradas)
```

---

## 🔒 INFORMACIÓN CONFIDENCIAL

### Presupuesto Detallado

```
(Mantener aquí información sensible de presupuesto)
```

### Compensación del Equipo

```
(Salarios y bonos - confidencial)
```

### Negociaciones con Hospital

```
(Detalles de negociación que no son públicos)
```

### Evaluaciones Personales

```
(Performance reviews privadas del equipo)
```

---

## 📊 DECISIONES PENDIENTES

```
1. Proveedor Cloud (AWS/Azure/DigitalOcean)
   Status: Abierto
   Deadline: 5 Nov
   Notas: Requiere análisis de costos

2. Modelo de escalabilidad post-MVP
   Status: Abierto
   Deadline: Después de Semana 6
   Notas: Re-evaluar con datos reales

3. Venta/Licencia del software
   Status: Pendiente definición legal
   Deadline: Antes de piloto
   Notas: Importante para futuro
```

---

**Última actualización:** 31 de Octubre, 2025  
**Rama:** `leads-only` (Acceso restringido)  
**Siguiente reunión:** (Por programar)
