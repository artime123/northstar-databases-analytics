# MongoDB Atlas Setup — Do This First (≈10 minutes)

You can start this **right now** while I build the code. It runs in the background.

---

## Step 1: Create a free Atlas account

1. Go to **https://www.mongodb.com/cloud/atlas/register**
2. Sign up with your email or Google account
3. Answer the onboarding questions however you like (it doesn't matter)

## Step 2: Create a free cluster

1. Choose **"M0 FREE"** tier (this is the free shared cluster — never expires)
2. Provider: **AWS** (default is fine)
3. Region: pick the one closest to you (e.g. `eu-west-1` Ireland or `eu-west-2` London)
4. Cluster name: leave as `Cluster0` or rename to `NorthStar`
5. Click **"Create Deployment"**
6. Wait ~3–5 minutes for it to provision

## Step 3: Create a database user

When prompted (or under **Database Access** in the left sidebar):

1. Username: `northstar_admin`
2. Password: click **"Autogenerate Secure Password"** — **COPY AND SAVE THIS PASSWORD SOMEWHERE YOU CAN FIND IT**
3. Built-in role: **"Atlas admin"** (for simplicity)
4. Click **"Add User"**

## Step 4: Allow network access

Under **Network Access** in the left sidebar:

1. Click **"Add IP Address"**
2. Click **"ALLOW ACCESS FROM ANYWHERE"** (this adds `0.0.0.0/0`)
3. Confirm

> ⚠️ This is fine for an academic project. For production you'd whitelist specific IPs.

## Step 5: Get your connection string

1. Go back to **Database** (left sidebar) → click **"Connect"** on your cluster
2. Choose **"Drivers"** → **Python** → version **3.12 or later**
3. Copy the connection string. It looks like this:

```
mongodb+srv://northstar_admin:<password>@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0
```

4. **Replace `<password>`** with the password you saved in Step 3
5. Save the full connection string somewhere — you'll paste it into the Colab notebook

## Step 6: (Optional) Install MongoDB Compass

Compass is the desktop GUI for MongoDB — useful for visually inspecting your data and running queries. **Optional but recommended:**

1. Download from **https://www.mongodb.com/products/compass**
2. Install, open it, paste the same connection string from Step 5
3. Click **Connect**
4. You'll see your cluster — empty for now, but data will appear once we insert it

---

## ✅ Done — what you should have

- [ ] An Atlas account
- [ ] A running M0 cluster called `Cluster0` (or `NorthStar`)
- [ ] A database user `northstar_admin` with a password you've saved
- [ ] Network access allowed from anywhere
- [ ] A connection string with the password substituted in

**Keep that connection string handy.** You'll paste it into the Colab notebook in Section 3.

If you hit any wall during setup, tell me which step and I'll help.
