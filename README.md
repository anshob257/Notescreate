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

- Set required environment variables (`SUPABASE_URL`, `SUPABASE_ANON_KEY`) in Supabase Functions.

## 🛠️ Schema Design (Why?)

- **Primary Key**: `id uuid` for unique identification.
- **user_id**: To associate notes to authenticated user.
- **title/content**: Text fields to store note details.
- **created_at**: Timestamp to sort notes by creation time.

## 📝 Demo Script

### Create a note (POST /notes)

```
curl -X POST https://<project-ref>.functions.supabase.co/post_notes \
 -H 'Authorization: Bearer <your-jwt>' \
 -H 'Content-Type: application/json' \
 -d '{"title": "Sample Note", "content": "This is a test note"}'
```

### List all notes (GET /notes)

```
curl -X GET https://<project-ref>.functions.supabase.co/get_notes \
 -H 'Authorization: Bearer <your-jwt>'
```