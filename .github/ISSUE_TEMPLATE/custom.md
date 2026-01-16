# P2P Exchange Backend (starter scaffold)

This repository is a starter scaffold for a P2P trading platform backend (Node.js + TypeScript + Express + Prisma + Postgres). It implements core flows: user auth, wallets, P2P offers, basic escrow (custodial) flow, deposit (mock) and withdrawal request (hook for PSP).

Important: This scaffold is for development and demonstration. Do NOT use in production without:
- KYC/AML integration & enforcement
- Payment processor / bank integrations for fiat rails
- Proper secrets management (HSM / Vault)
- Security audits & hardened infra
- Legal counsel for licensing in your jurisdictions

Quickstart (dev)
1. Copy `.env.example` to `.env` and adjust values.
2. Start DB and backend:
   docker-compose up --build
3. Run Prisma migrations:
   npx prisma migrate dev --name init
4. API will be available at http://localhost:4000

Key endpoints
- POST /api/auth/register
- POST /api/auth/login
- GET /api/wallets
- POST /api/wallets/deposit
- POST /api/wallets/withdraw
- GET /api/offers
- POST /api/offers
- POST /api/offers/:id/accept
- POST /api/offers/:id/release
- POST /api/payments/onboard
- POST /api/payments/charge

Security & production notes
- Rotate any secret keys that were shared publicly and never store secrets in the repo.
- Use Vault / AWS Secrets Manager / GCP Secret Manager for secrets.
- Enforce KYC (Sumsub) before allowing trading/withdrawals.
- Integrate a custody provider (Fireblocks/BitGo) for on-chain movements.
- Conduct penetration testing and compliance audits before processing real funds.

For help pushing these files and configuring GitHub secrets or CI, ask me to walk you through any step.


