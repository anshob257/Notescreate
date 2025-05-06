# Custom Notes Service

A minimal Supabase backend for personal notes service.

## 📂 Setup & Deploy Steps

- Create a Supabase project.
- Create the `notes` table by running:

```
supabase db remote set <project-connection-string>
supabase db push
```

- Deploy functions:

```
supabase functions deploy post_notes
supabase functions deploy get_notes
```

- Set required environment variables (https://znzabgsahhgnseoqxikz.supabase.co, eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InpuemFiZ3NhaGhnbnNlb3F4aWt6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDYwMTMwNDMsImV4cCI6MjA2MTU4OTA0M30.CfKR6FQMjrY6LcwYaF_999km8LsHRhb0Cfyzqk6eObQ) in Supabase Functions.

## 🛠️ Schema Design (Why?)

- **Primary Key**: `id uuid` for unique identification.
- **user_id**: To associate notes to authenticated user.
- **title/content**: Text fields to store note details.
- **created_at**: Timestamp to sort notes by creation time.

## 📝 Demo Script

### Create a note (POST /notes)

```
curl -L -X POST 'https://znzabgsahhgnseoqxikz.supabase.co/functions/v1/post_notes' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InpuemFiZ3NhaGhnbnNlb3F4aWt6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDYwMTMwNDMsImV4cCI6MjA2MTU4OTA0M30.CfKR6FQMjrY6LcwYaF_999km8LsHRhb0Cfyzqk6eObQ' \
  -H 'Content-Type: application/json' \
  --data '{"name":"Functions"}'

```

### List all notes (GET /notes)

```
curl -L -X POST 'https://znzabgsahhgnseoqxikz.supabase.co/functions/v1/get_notes' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InpuemFiZ3NhaGhnbnNlb3F4aWt6Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NDYwMTMwNDMsImV4cCI6MjA2MTU4OTA0M30.CfKR6FQMjrY6LcwYaF_999km8LsHRhb0Cfyzqk6eObQ' \
  -H 'Content-Type: application/json' \
  --data '{"name":"Functions"}'
```