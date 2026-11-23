# QUIZ BATTLE BD

Mobile-first Telegram Mini App starter, black-purple UI, Bangla/English quiz, admin dashboard, Supabase schema and Edge Functions, Telegram bot webhook, Vercel static hosting.

## Setup
1. Create Supabase project; run `supabase/schema.sql` in SQL Editor.
2. Create an Admin user in Supabase Auth, then add their UUID: `insert into public.admin_users(user_id) values ('AUTH-USER-UUID');`
3. Edit `js/config.js` with Supabase Project URL, anon/publishable key and Functions URL. Never add service_role or Bot Token there.
4. Supabase Edge Function secrets: `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_ROLE_KEY`, `TELEGRAM_BOT_TOKEN`, `AUTH_SALT` (random secret), `MINI_APP_URL`, `TELEGRAM_WEBHOOK_SECRET`.
5. Deploy functions with Supabase CLI: `supabase functions deploy telegram-auth quiz-engine battle-engine bot-webhook bot-broadcast`.
6. Set Telegram webhook to `https://PROJECT.supabase.co/functions/v1/bot-webhook` and configure Mini App URL in BotFather.
7. Deploy this folder to Vercel. Add questions in Admin Panel.

## Important status
- Quiz flow and category/question/level management are scaffolded.
- Battle function currently matches/creates waiting rooms only; realtime match gameplay and anti-cheat are not yet implemented.
- Premium plan/payment schema is included, but Stars invoice creation, pre_checkout_query approval and successful-payment routing must be completed before selling subscriptions.
- Ad placement settings are represented in schema; integrate a provider SDK and server-verified rewarded callbacks before awarding coins.
- Review and test RLS and all Edge Functions in a staging project before public launch.
- Telegram `initData` signature is checked server-side. Never trust `initDataUnsafe` for identity.
