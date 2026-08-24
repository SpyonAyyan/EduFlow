# EduFlow — Modern AI-Powered School & Academy Management SaaS

EduFlow is a production-grade, multi-tenant Educational Management Information System (EMIS) built with Flutter, Riverpod, GoRouter, Supabase, and PostgreSQL.

---

## 🌟 Architecture & Highlights

- **Multi-Tenant SaaS Foundation:** Strict organization isolation via PostgreSQL Row Level Security (RLS) policies and `organization_members`.
- **Organization Code Authentication:** Seamless login via `Organization Code` (e.g. `BEACON-7X92`), `Email/Username`, and `Password`. No post-login workspace selector.
- **Organization Code Join Requests:** Unauthenticated or new users can enter an Organization Code to request membership for admin approval.
- **Role-Based Portals:** Custom interfaces tailored for Super Admin, School Admin, Academic Coordinator, Class/Subject Teachers, Students, and Parents.
- **Responsive & Cross-Platform UI:** Single Flutter codebase supporting Android, iOS, Windows, macOS, and Web.

---

## 🗄️ Database Schema & RLS (`supabase/schema_v3.sql`)

Run the full `supabase/schema_v3.sql` script inside your Supabase SQL Editor.

Key tables:
- `organizations` (`id`, `organization_code`, `name`, `subscription_status`)
- `profiles` (`id`, `auth_user_id`, `organization_id`, `full_name`, `email`, `role`)
- `organization_members` (`id`, `organization_id`, `user_id`, `role`, `status`)
- `join_requests` (`id`, `organization_id`, `applicant_name`, `applicant_email`, `requested_role`, `status`)
- `classes`, `sections`, `subjects`, `class_teacher_assignments`, `subject_teacher_assignments`
- `students`, `parent_student_relationships`, `attendance`, `exams`, `exam_marks`, `fee_invoices`, `payments`, `homework`, `timetables`, `announcements`, `notifications`, `audit_logs`

---

## 🔑 Demo Login Credentials

Below are default demo accounts configured for testing with default organization code `BEACON-7X92`:

| Role | Organization Code | Email / Username | Password |
| :--- | :--- | :--- | :--- |
| **Super Admin** | *N/A (Platform Admin)* | `admin@eduflow.com` | `admin123` |
| **School Admin** | `BEACON-7X92` | `principal@school.com` | `admin123` |
| **Teacher** | `BEACON-7X92` | `teacher@school.com` | `teacher123` |
| **Student** | `BEACON-7X92` | `student@school.com` | `student123` |

---

## 🛠️ Getting Started & Testing

### 1. Run Flutter App
```bash
flutter pub get
flutter run -d chrome  # or windows / android
```

### 2. Run Tests
```bash
flutter test
```

### 3. Run Linter / Static Analysis
```bash
flutter analyze
```

---

## 🚀 Deployment Instructions

1. **Supabase Setup:** Execute `supabase/schema_v3.sql` in your Supabase project.
2. **Environment Configuration:** Update `lib/main.dart` with your Supabase URL and anon publishable key.
3. **Build Web & Windows:**
```bash
flutter build web --release
flutter build windows --release
```
