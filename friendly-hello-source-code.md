# Friendly Hello (My Life) — Core Source Code

**Live Deployment:** https://smiles-galore.lovable.app/

**Project ID:** 62d20b24-3dda-443a-9893-82b9a9d0dfc1

---

## File: `src/routes/index.tsx`

```tsx
import { createFileRoute, Link } from "@tanstack/react-router";
import { HeartPulse, Languages, Mic, PhoneCall, Sparkles } from "lucide-react";
import { Logo } from "@/components/brand/Logo";
import { Button } from "@/components/ui/button";

export const Route = createFileRoute("/")({
  head: () => ({
    meta: [
      { title: "My Life — Your AI Health Companion" },
      { name: "description", content: "Ask health questions in plain words, understand symptoms, get clear next steps, and reach someone you trust." },
      { property: "og:title", content: "My Life — Your AI Health Companion" },
      { property: "og:description", content: "Ask health questions in plain words, understand symptoms, get clear next steps, and reach someone you trust." },
    ],
  }),
  component: Landing,
});

function Landing() {
  return (
    <div className="min-h-dvh bg-bg">
      <header className="mx-auto flex max-w-6xl items-center justify-between px-5 py-5">
        <Logo />
        <div className="flex gap-2">
          <Button asChild variant="ghost" size="sm">
            <Link to="/auth">Sign in</Link>
          </Button>
          <Button asChild size="sm">
            <Link to="/auth">Try My Life</Link>
          </Button>
        </div>
      </header>

      <section className="mx-auto grid max-w-6xl gap-10 px-5 pb-16 pt-8 md:grid-cols-2 md:items-center md:pt-16">
        <div>
          <p className="text-sm font-medium uppercase tracking-[0.16em] text-primary">
            Your AI Health Companion
          </p>
          <h1 className="font-display mt-3 text-4xl font-semibold leading-[1.12] tracking-tight text-ink md:text-5xl">
            Health information, made simple.
          </h1>
          <p className="mt-4 max-w-md text-lg leading-relaxed text-muted">
            Ask questions. Understand your symptoms. Get clear next steps. Connect with someone you
            trust.
          </p>
          <div className="mt-8 flex flex-wrap gap-3">
            <Button asChild size="lg">
              <Link to="/auth">Try My Life</Link>
            </Button>
            <Button asChild size="lg" variant="outline">
              <a href="#how">See how it works</a>
            </Button>
          </div>
          <p className="mt-6 max-w-md text-sm text-subtle">
            My Life does not diagnose illness and does not replace a doctor. It helps you understand
            information and decide what to do next.
          </p>
        </div>
        <div className="rounded-xl border border-line bg-surface p-5 shadow-card">
          <p className="text-xs font-semibold uppercase tracking-wide text-muted">Ask My Life</p>
          <p className="mt-3 rounded-lg bg-primary-soft px-4 py-3 text-sm leading-relaxed text-primary-dark">
            Fever and cough can happen with several common illnesses. Chat cannot diagnose the cause.
            How long have you had the fever, and do you have any difficulty breathing?
          </p>
          <div className="mt-4 grid gap-2">
            {["What you can do now", "Watch for these signs", "When to seek care"].map((s) => (
              <div key={s} className="rounded-md border border-line px-3 py-2 text-sm">
                {s}
              </div>
            ))}
          </div>
        </div>
      </section>

      <section id="how" className="border-y border-line bg-surface">
        <div className="mx-auto grid max-w-6xl gap-8 px-5 py-14 md:grid-cols-3">
          {[
            { n: "01", t: "Ask AI", d: "Type or speak in everyday words — fever, tiredness, or “I don’t know what to ask.”" },
            { n: "02", t: "Understand", d: "Get simple explanations, follow-up questions, and warning signs — never a fake diagnosis." },
            { n: "03", t: "Take the next step", d: "Call, message a trusted person, or visit a clinic when that is the safer choice." },
          ].map((s) => (
            <div key={s.n}>
              <p className="font-display text-3xl text-primary">{s.n}</p>
              <h2 className="mt-2 font-display text-xl font-semibold">{s.t}</h2>
              <p className="mt-2 text-sm leading-relaxed text-muted">{s.d}</p>
            </div>
          ))}
        </div>
      </section>

      <section className="mx-auto max-w-6xl px-5 py-16">
        <h2 className="font-display max-w-xl text-3xl font-semibold tracking-tight">
          Built for people, not medical jargon.
        </h2>
        <div className="mt-8 grid gap-4 sm:grid-cols-2 lg:grid-cols-3">
          {[
            { icon: Languages, t: "Local languages", d: "English, Hindi, Tamil, Telugu, Kannada, Malayalam, Bengali, Marathi." },
            { icon: Mic, t: "Voice support", d: "Speak your question when typing is hard." },
            { icon: PhoneCall, t: "Emergency connection", d: "One tap to call services or WhatsApp a trusted contact." },
            { icon: HeartPulse, t: "Personalized cautions", d: "Optional profile use for allergies and medicines — only with your permission." },
            { icon: Sparkles, t: "Simple explanations", d: "Short cards: what it could mean, what to do now, when to get help." },
          ].map((f) => (
            <div key={f.t} className="rounded-lg border border-line bg-surface p-5">
              <f.icon className="size-5 text-primary" />
              <h3 className="mt-3 font-medium">{f.t}</h3>
              <p className="mt-1 text-sm text-muted leading-relaxed">{f.d}</p>
            </div>
          ))}
        </div>
      </section>

      <footer className="border-t border-line bg-surface px-5 py-10">
        <div className="mx-auto flex max-w-6xl flex-col gap-6 md:flex-row md:justify-between">
          <div>
            <Logo />
            <p className="mt-2 text-sm text-muted">AI health information and support.</p>
          </div>
          <div className="flex flex-wrap gap-4 text-sm">
            <Link to="/privacy" className="text-muted hover:text-ink">
              Privacy
            </Link>
            <Link to="/safety" className="text-muted hover:text-ink">
              Safety
            </Link>
            <Link to="/terms" className="text-muted hover:text-ink">
              Terms
            </Link>
            <a href="mailto:hello@mylife.health" className="text-muted hover:text-ink">
              Contact
            </a>
          </div>
        </div>
        <p className="mx-auto mt-8 max-w-6xl text-xs text-subtle">
          My Life provides general health information and does not replace professional medical
          advice.
        </p>
      </footer>
    </div>
  );
}

```

---

## File: `src/lib/store.ts`

```tsx
import { create } from "zustand";
import { persist } from "zustand/middleware";
import {
  emptyProfile,
  type ChatMessage,
  type Lang,
  type Profile,
  type Reminder,
  type Session,
  type VitalEntry,
} from "./types";
import { sha256, uid } from "./utils";

type Cred = { name: string; passHash: string };

type State = {
  hydrated: boolean;
  session: Session | null;
  language: Lang;
  useProfileForAI: boolean;
  users: Record<string, Cred>;
  profiles: Record<string, Profile>;
  chats: Record<string, ChatMessage[]>;
  reminders: Record<string, Reminder[]>;
  vitals: Record<string, VitalEntry[]>;
  setHydrated: (v: boolean) => void;
  setLanguage: (l: Lang) => void;
  setUseProfileForAI: (v: boolean) => void;
  signup: (name: string, identifier: string, password: string) => Promise<string | null>;
  login: (identifier: string, password: string) => Promise<string | null>;
  guest: () => void;
  demo: () => void;
  logout: () => void;
  saveProfile: (p: Profile) => void;
  profile: () => Profile;
  messages: () => ChatMessage[];
  addMessage: (m: ChatMessage) => void;
  setMessages: (m: ChatMessage[]) => void;
  clearChat: () => void;
  addReminder: (r: Omit<Reminder, "id">) => void;
  toggleReminder: (id: string) => void;
  removeReminder: (id: string) => void;
  userReminders: () => Reminder[];
  markReminderFired: (id: string, key: string) => void;
  addVital: (v: Omit<VitalEntry, "id" | "createdAt">) => void;
  removeVital: (id: string) => void;
  userVitals: () => VitalEntry[];
  clearHealthData: () => void;
  deleteAccount: () => void;
};

function demoProfile(): Profile {
  return {
    name: "Arun",
    age: "28",
    gender: "Male",
    bloodGroup: "O+",
    allergies: "None listed",
    medicines: "None listed",
    conditions: "None listed",
    notes: "Demo profile — replace with your own details.",
    emergencyName: "Priya",
    emergencyPhone: "+919876543210",
    emergencyRelation: "Sister",
  };
}

export const useAppStore = create<State>()(
  persist(
    (set, get) => ({
      hydrated: false,
      session: null,
      language: "en",
      useProfileForAI: false,
      users: {},
      profiles: {},
      chats: {},
      reminders: {},
      vitals: {},
      setHydrated: (v) => set({ hydrated: v }),
      setLanguage: (language) => set({ language }),
      setUseProfileForAI: (useProfileForAI) => set({ useProfileForAI }),
      signup: async (name, identifier, password) => {
        const id = identifier.trim().toLowerCase();
        if (!id || !name.trim() || password.length < 4) return "Please fill every field (password at least 4 characters).";
        if (get().users[id]) return "An account with this mobile or email already exists.";
        const passHash = await sha256(password);
        const userId = uid("u");
        set((s) => ({
          users: { ...s.users, [id]: { name: name.trim(), passHash } },
          session: { id: userId, name: name.trim(), identifier: id, isGuest: false, isDemo: false },
          profiles: {
            ...s.profiles,
            [userId]: { ...emptyProfile(), name: name.trim() },
          },
        }));
        return null;
      },
      login: async (identifier, password) => {
        const id = identifier.trim().toLowerCase();
        const rec = get().users[id];
        const passHash = await sha256(password);
        if (!rec || rec.passHash !== passHash) {
          return "Check your mobile/email and password. This is demo sign-in stored only in this browser.";
        }
        const existing = Object.values(get().profiles).find((p) => p.name === rec.name);
        const userId = uid("u");
        set({
          session: { id: userId, name: rec.name, identifier: id, isGuest: false, isDemo: false },
          profiles: {
            ...get().profiles,
            [userId]: existing ?? { ...emptyProfile(), name: rec.name },
          },
        });
        return null;
      },
      guest: () => {
        const userId = uid("guest");
        set({
          session: { id: userId, name: "Guest", identifier: "guest", isGuest: true, isDemo: false },
          profiles: { ...get().profiles, [userId]: emptyProfile() },
        });
      },
      demo: () => {
        const userId = "demo_arun";
        set({
          session: {
            id: userId,
            name: "Arun",
            identifier: "demo@mylife.app",
            isGuest: false,
            isDemo: true,
          },
          profiles: { ...get().profiles, [userId]: demoProfile() },
        });
      },
      logout: () => set({ session: null }),
      saveProfile: (p) => {
        const s = get().session;
        if (!s) return;
        set({ profiles: { ...get().profiles, [s.id]: p } });
        if (p.name && p.name !== s.name) {
          set({ session: { ...s, name: p.name } });
        }
      },
      profile: () => {
        const s = get().session;
        if (!s) return emptyProfile();
        return get().profiles[s.id] ?? emptyProfile();
      },
      messages: () => {
        const s = get().session;
        if (!s) return [];
        return get().chats[s.id] ?? [];
      },
      addMessage: (m) => {
        const s = get().session;
        if (!s) return;
        const prev = get().chats[s.id] ?? [];
        set({ chats: { ...get().chats, [s.id]: [...prev, m] } });
      },
      setMessages: (m) => {
        const s = get().session;
        if (!s) return;
        set({ chats: { ...get().chats, [s.id]: m } });
      },
      clearChat: () => {
        const s = get().session;
        if (!s) return;
        set({ chats: { ...get().chats, [s.id]: [] } });
      },
      addReminder: (r) => {
        const s = get().session;
        if (!s) return;
        const prev = get().reminders[s.id] ?? [];
        set({
          reminders: {
            ...get().reminders,
            [s.id]: [...prev, { ...r, id: uid("rem") }],
          },
        });
      },
      toggleReminder: (id) => {
        const s = get().session;
        if (!s) return;
        const prev = get().reminders[s.id] ?? [];
        set({
          reminders: {
            ...get().reminders,
            [s.id]: prev.map((x) => (x.id === id ? { ...x, enabled: !x.enabled } : x)),
          },
        });
      },
      removeReminder: (id) => {
        const s = get().session;
        if (!s) return;
        const prev = get().reminders[s.id] ?? [];
        set({
          reminders: {
            ...get().reminders,
            [s.id]: prev.filter((x) => x.id !== id),
          },
        });
      },
      userReminders: () => {
        const s = get().session;
        if (!s) return [];
        return get().reminders[s.id] ?? [];
      },
      markReminderFired: (id, key) => {
        const s = get().session;
        if (!s) return;
        const prev = get().reminders[s.id] ?? [];
        set({
          reminders: {
            ...get().reminders,
            [s.id]: prev.map((x) => (x.id === id ? { ...x, lastFired: key } : x)),
          },
        });
      },
      addVital: (v) => {
        const s = get().session;
        if (!s) return;
        const prev = get().vitals[s.id] ?? [];
        set({
          vitals: {
            ...get().vitals,
            [s.id]: [...prev, { ...v, id: uid("vit"), createdAt: Date.now() }],
          },
        });
      },
      removeVital: (id) => {
        const s = get().session;
        if (!s) return;
        const prev = get().vitals[s.id] ?? [];
        set({ vitals: { ...get().vitals, [s.id]: prev.filter((x) => x.id !== id) } });
      },
      userVitals: () => {
        const s = get().session;
        if (!s) return [];
        return get().vitals[s.id] ?? [];
      },
      clearHealthData: () => {
        const s = get().session;
        if (!s) return;
        set({
          profiles: { ...get().profiles, [s.id]: { ...emptyProfile(), name: s.name } },
          chats: { ...get().chats, [s.id]: [] },
          reminders: { ...get().reminders, [s.id]: [] },
          vitals: { ...get().vitals, [s.id]: [] },
          useProfileForAI: false,
        });
      },
      deleteAccount: () => {
        const s = get().session;
        if (!s) return;
        const users = { ...get().users };
        delete users[s.identifier];
        const profiles = { ...get().profiles };
        delete profiles[s.id];
        const chats = { ...get().chats };
        delete chats[s.id];
        const reminders = { ...get().reminders };
        delete reminders[s.id];
        const vitals = { ...get().vitals };
        delete vitals[s.id];
        set({ session: null, users, profiles, chats, reminders, vitals });
      },
    }),
    {
      name: "mylife-v1",
      partialize: (s) => ({
        session: s.session,
        language: s.language,
        useProfileForAI: s.useProfileForAI,
        users: s.users,
        profiles: s.profiles,
        chats: s.chats,
        reminders: s.reminders,
        vitals: s.vitals,
      }),
    },
  ),
);

```

---

## File: `src/routes/app/index.tsx`

```tsx
import { createFileRoute, Link, useNavigate } from "@tanstack/react-router";
import { BookOpen, Mic, PhoneCall, Stethoscope, User } from "lucide-react";
import { useMemo, useState } from "react";
import { toast } from "sonner";
import { Button } from "@/components/ui/button";
import { Card, CardDesc, CardTitle } from "@/components/ui/card";
import { TIPS } from "@/lib/content";
import { t } from "@/lib/i18n";
import { sendHealthQuestion } from "@/lib/chat-send";
import { useAppStore } from "@/lib/store";

export const Route = createFileRoute("/app/")({
  head: () => ({
    meta: [
      { title: "Home — My Life" },
      { name: "description", content: "Your daily health home: ask a question, read a tip, and check reminders." },
      { property: "og:title", content: "Home — My Life" },
      { property: "og:description", content: "Your daily health home: ask a question, read a tip, and check reminders." },
    ],
  }),
  component: Dashboard,
});

const EXAMPLES = [
  "I have a fever",
  "I have a headache",
  "Why am I feeling tired?",
  "What should I eat today?",
  "When should I see a doctor?",
];

function Dashboard() {
  const session = useAppStore((s) => s.session)!;
  const lang = useAppStore((s) => s.language);
  const [q, setQ] = useState("");
  const [busy, setBusy] = useState(false);
  const [guide, setGuide] = useState(false);
  const nav = useNavigate();
  const tip = useMemo(() => TIPS[new Date().getDate() % TIPS.length], []);

  async function go(text: string) {
    const msg = text.trim();
    if (!msg) return;
    setBusy(true);
    try {
      await sendHealthQuestion(msg);
      nav({ to: "/app/chat" });
    } catch {
      toast.error("Could not send. Try again.");
    } finally {
      setBusy(false);
    }
  }

  function voice() {
    const SR = (window as unknown as { webkitSpeechRecognition?: new () => SpeechRecognition }).webkitSpeechRecognition
      || (window as unknown as { SpeechRecognition?: new () => SpeechRecognition }).SpeechRecognition;
    if (!SR) {
      toast.message(t(lang, "voiceUnsupported"));
      return;
    }
    const rec = new SR();
    rec.lang = lang === "hi" ? "hi-IN" : lang === "ta" ? "ta-IN" : "en-IN";
    rec.onresult = (e: SpeechRecognitionEvent) => {
      const said = e.results[0]?.[0]?.transcript ?? "";
      setQ(said);
    };
    rec.start();
    toast.message(t(lang, "listening"));
  }

  return (
    <div className="mx-auto max-w-3xl space-y-6">
      <div>
        <h1 className="font-display text-3xl font-semibold tracking-tight">
          {t(lang, "greeting", { name: session.name })}
        </h1>
        <p className="mt-1 text-muted">{t(lang, "helpToday")}</p>
        {session.isDemo ? (
          <p className="mt-2 text-xs text-warn">Demo data (Arun). Replace it with your own details anytime.</p>
        ) : null}
      </div>

      <Card className="p-5">
        <CardTitle>{t(lang, "askTitle")}</CardTitle>
        <textarea
          className="mt-3 w-full resize-none rounded-md border border-line bg-bg px-3.5 py-3 text-base"
          rows={3}
          placeholder={t(lang, "askPlaceholder")}
          value={q}
          onChange={(e) => setQ(e.target.value)}
        />
        <div className="mt-3 flex flex-wrap gap-2">
          <Button type="button" variant="outline" onClick={voice}>
            <Mic className="size-4" /> {t(lang, "voice")}
          </Button>
          <Button type="button" disabled={busy} onClick={() => go(q)}>
            {t(lang, "askAi")}
          </Button>
        </div>
        <div className="mt-4 flex flex-wrap gap-2">
          {EXAMPLES.map((ex) => (
            <button
              key={ex}
              className="rounded-full border border-line bg-surface px-3 py-1.5 text-sm text-muted hover:text-ink"
              onClick={() => go(ex)}
              type="button"
            >
              {ex}
            </button>
          ))}
        </div>
      </Card>

      <Button variant="soft" className="w-full" onClick={() => setGuide(true)}>
        {t(lang, "dontKnow")}
      </Button>
      {guide ? <DontKnow onDone={(text) => go(text)} /> : null}

      <div className="grid gap-3 sm:grid-cols-2">
        <Quick to="/app/symptoms" icon={Stethoscope} title="Check symptoms" desc="A few simple questions, then clear next steps." />
        <Quick to="/app/profile" icon={User} title="Health profile" desc="Save details so guidance can be more relevant." />
        <Quick to="/app/emergency" icon={PhoneCall} title="Emergency contact" desc="Call or WhatsApp someone you trust." />
        <Quick to="/app/awareness" icon={BookOpen} title="Health awareness" desc="Short, plain-language topics." />
      </div>

      <Card>
        <CardTitle>{t(lang, "tipTitle")}</CardTitle>
        <CardDesc className="mt-2">{tip}</CardDesc>
      </Card>
    </div>
  );
}

function Quick({
  to,
  icon: Icon,
  title,
  desc,
}: {
  to: string;
  icon: typeof User;
  title: string;
  desc: string;
}) {
  return (
    <Link to={to} className="block rounded-xl border border-line bg-surface p-5 shadow-card hover:border-primary/40">
      <Icon className="size-5 text-primary" />
      <p className="mt-3 font-medium">{title}</p>
      <p className="mt-1 text-sm text-muted">{desc}</p>
    </Link>
  );
}

function DontKnow({ onDone }: { onDone: (t: string) => void }) {
  const [feeling, setFeeling] = useState("");
  const [when, setWhen] = useState("");
  const [bad, setBad] = useState("moderate");
  const [elseu, setElse] = useState("");
  return (
    <Card>
      <CardTitle>My Life will help you explain what you are feeling.</CardTitle>
      <div className="mt-4 space-y-3">
        <Field label="What are you feeling?" value={feeling} onChange={setFeeling} />
        <Field label="When did it start?" value={when} onChange={setWhen} />
        <div>
          <p className="mb-1.5 text-sm font-medium text-muted">How bad is it?</p>
          <div className="flex gap-2">
            {["mild", "moderate", "severe"].map((x) => (
              <button
                key={x}
                type="button"
                onClick={() => setBad(x)}
                className={`min-h-11 flex-1 rounded-md border text-sm capitalize ${bad === x ? "border-primary bg-primary-soft text-primary-dark" : "border-line"}`}
              >
                {x}
              </button>
            ))}
          </div>
        </div>
        <Field label="Anything else unusual?" value={elseu} onChange={setElse} />
        <Button
          className="w-full"
          onClick={() =>
            onDone(
              `I don't know what to ask. I feel: ${feeling || "not sure"}. Started: ${when || "not sure"}. Severity: ${bad}. Other: ${elseu || "none"}.`,
            )
          }
        >
          Continue with AI
        </Button>
      </div>
    </Card>
  );
}

function Field({
  label,
  value,
  onChange,
}: {
  label: string;
  value: string;
  onChange: (v: string) => void;
}) {
  return (
    <label className="block">
      <span className="mb-1.5 block text-sm font-medium text-muted">{label}</span>
      <input
        className="h-11 w-full rounded-md border border-line px-3"
        value={value}
        onChange={(e) => onChange(e.target.value)}
      />
    </label>
  );
}

type SpeechRecognition = {
  lang: string;
  start: () => void;
  onresult: ((e: SpeechRecognitionEvent) => void) | null;
};
type SpeechRecognitionEvent = { results: { 0: { 0: { transcript: string } } } };

```

---

## File: `src/routes/app/chat.tsx`

```tsx
import { createFileRoute, Link } from "@tanstack/react-router";
import { Mic, Send, Share2 } from "lucide-react";
import { useEffect, useRef, useState } from "react";
import { toast } from "sonner";
import { GuidanceCards } from "@/components/chat/GuidanceCards";
import { Button } from "@/components/ui/button";
import { Switch } from "@/components/ui/switch";
import { sendHealthQuestion } from "@/lib/chat-send";
import { seedWelcome } from "@/lib/ai/mock";
import { t } from "@/lib/i18n";
import { emptyProfile } from "@/lib/types";
import { useAppStore } from "@/lib/store";
import { waLink } from "@/lib/utils";
import { cn } from "@/lib/utils";

export const Route = createFileRoute("/app/chat")({
  head: () => ({
    meta: [
      { title: "AI Health Chat — My Life" },
      { name: "description", content: "Chat with My Life about symptoms and get simple explanations and next steps." },
      { property: "og:title", content: "AI Health Chat — My Life" },
      { property: "og:description", content: "Chat with My Life about symptoms and get simple explanations and next steps." },
    ],
  }),
  component: ChatPage,
});

const SHORTCUTS = [
  { k: "explain", labelKey: "explainSimply" as const, simple: true },
  { k: "wrong", labelKey: "notSure" as const },
  { k: "doc", labelKey: "seeDoctor" as const },
  { k: "serious", labelKey: "serious" as const },
  { k: "prevent", labelKey: "prevent" as const },
];

function ChatPage() {
  const lang = useAppStore((s) => s.language);
  const sessionId = useAppStore((s) => s.session?.id);
  const messages = useAppStore((s) => (sessionId ? s.chats[sessionId] : undefined)) ?? [];
  const addMessage = useAppStore((s) => s.addMessage);
  const useProfile = useAppStore((s) => s.useProfileForAI);
  const setUse = useAppStore((s) => s.setUseProfileForAI);
  const profile = useAppStore((s) => (sessionId ? s.profiles[sessionId] : undefined)) ?? emptyProfile();
  const [text, setText] = useState("");
  const [busy, setBusy] = useState(false);
  const [shareOpen, setShareOpen] = useState(false);
  const end = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (messages.length === 0) addMessage(seedWelcome());
  }, [messages.length, addMessage]);

  useEffect(() => {
    end.current?.scrollIntoView({ behavior: "smooth" });
  }, [messages, busy]);

  async function send(raw?: string, simple?: boolean) {
    const msg = (raw ?? text).trim();
    if (!msg || busy) return;
    setText("");
    setBusy(true);
    try {
      await sendHealthQuestion(msg, { simple });
    } catch {
      toast.error("The assistant could not reply. Try again.");
    } finally {
      setBusy(false);
    }
  }

  function voice() {
    const w = window as unknown as {
      webkitSpeechRecognition?: new () => Rec;
      SpeechRecognition?: new () => Rec;
    };
    const SR = w.SpeechRecognition || w.webkitSpeechRecognition;
    if (!SR) {
      toast.message(t(lang, "voiceUnsupported"));
      return;
    }
    const rec = new SR();
    rec.lang = lang === "en" ? "en-IN" : `${lang}-IN`;
    rec.onresult = (e) => setText(e.results[0][0].transcript);
    rec.start();
    toast.message(t(lang, "listening"));
  }

  const lastAi = [...messages].reverse().find((m) => m.role === "assistant");
  const lastUser = [...messages].reverse().find((m) => m.role === "user");
  const phone = profile.emergencyPhone;

  function share(kind: "q" | "a" | "all" | "em") {
    if (!phone) {
      toast.message(t(lang, "emptyContact"));
      return;
    }
    let body = "Message from My Life (general information, not a diagnosis).\n";
    if (kind === "q") body += lastUser?.text ?? "";
    if (kind === "a") body += lastAi?.text ?? "";
    if (kind === "all")
      body += messages.map((m) => `${m.role === "user" ? "Me" : "My Life"}: ${m.text}`).join("\n");
    if (kind === "em")
      body = "Hi, I may need your help. Please contact me or help me reach medical care.";
    window.open(waLink(phone, body), "_blank");
  }

  return (
    <div className="mx-auto flex h-[calc(100dvh-10rem)] max-w-3xl flex-col md:h-[calc(100dvh-8rem)]">
      <div className="mb-3 flex items-start justify-between gap-3">
        <div>
          <h1 className="font-display text-2xl font-semibold">My Life AI</h1>
          <p className="text-sm text-muted">Health information and support</p>
        </div>
        <Button variant="outline" size="sm" onClick={() => setShareOpen((v) => !v)}>
          <Share2 className="size-4" /> Share
        </Button>
      </div>
      <p className="mb-3 rounded-md bg-warn-soft px-3 py-2 text-xs text-warn">{t(lang, "disclaimer")}</p>

      <label className="mb-3 flex items-center justify-between gap-3 rounded-md border border-line bg-surface px-3 py-2 text-sm">
        <span>{t(lang, "useProfile")}</span>
        <Switch checked={useProfile} onCheckedChange={setUse} />
      </label>

      {shareOpen ? (
        <div className="mb-3 grid gap-2 rounded-md border border-line bg-surface p-3 text-sm">
          <p className="font-medium">Share with someone you trust</p>
          <div className="flex flex-wrap gap-2">
            <Button size="sm" variant="outline" onClick={() => share("q")}>
              Current question
            </Button>
            <Button size="sm" variant="outline" onClick={() => share("a")}>
              AI response
            </Button>
            <Button size="sm" variant="outline" onClick={() => share("all")}>
              Whole conversation
            </Button>
            <Button size="sm" variant="whatsapp" onClick={() => share("em")}>
              Emergency message
            </Button>
          </div>
        </div>
      ) : null}

      <div className="min-h-0 flex-1 space-y-3 overflow-y-auto pr-1">
        {messages.length === 0 ? (
          <p className="py-10 text-center text-muted">{t(lang, "emptyChat")}</p>
        ) : null}
        {messages.map((m) => (
          <div key={m.id} className={cn("flex", m.role === "user" ? "justify-end" : "justify-start")}>
            <div
              className={cn(
                "max-w-[88%] rounded-lg px-4 py-3 text-sm leading-relaxed",
                m.role === "user" ? "rounded-br-sm bg-primary text-primary-fg" : "rounded-bl-sm border border-line bg-surface",
                m.emergency && "border-danger bg-danger-soft text-danger",
              )}
            >
              {m.role === "assistant" ? (
                <p className="mb-1 text-[11px] font-semibold uppercase tracking-wide text-primary">My Life</p>
              ) : null}
              <p>{m.text}</p>
              {m.sections ? <GuidanceCards sections={m.sections} /> : null}
              {m.emergency ? (
                <div className="mt-3 space-y-2">
                  <p className="font-semibold">{t(lang, "emergencyBanner")}</p>
                  <p>{t(lang, "seekNow")}</p>
                  <div className="flex flex-wrap gap-2">
                    <Button asChild size="sm" variant="danger">
                      <a href="tel:108">{t(lang, "call")} 108</a>
                    </Button>
                    <Button asChild size="sm" variant="whatsapp">
                      <Link to="/app/emergency">{t(lang, "message")}</Link>
                    </Button>
                  </div>
                </div>
              ) : null}
            </div>
          </div>
        ))}
        {busy ? (
          <div className="flex items-center gap-2 text-sm text-muted">
            <span className="think-dot">•</span>
            <span className="think-dot">•</span>
            <span className="think-dot">•</span>
            {t(lang, "thinking")}
          </div>
        ) : null}
        <div ref={end} />
      </div>

      <div className="mt-3 flex gap-2 overflow-x-auto pb-1">
        {SHORTCUTS.map((s) => (
          <button
            key={s.k}
            type="button"
            className="shrink-0 rounded-full border border-line bg-surface px-3 py-2 text-xs"
            onClick={() => send(t(lang, s.labelKey), s.simple)}
          >
            {t(lang, s.labelKey)}
          </button>
        ))}
      </div>
      <form
        className="mt-2 flex items-end gap-2"
        onSubmit={(e) => {
          e.preventDefault();
          send();
        }}
      >
        <Button type="button" variant="outline" size="icon" aria-label={t(lang, "voice")} onClick={voice}>
          <Mic className="size-4" />
        </Button>
        <input
          className="h-12 min-w-0 flex-1 rounded-full border border-line bg-surface px-4 text-base"
          placeholder="Type your health question..."
          value={text}
          onChange={(e) => setText(e.target.value)}
          aria-label="Health question"
        />
        <Button type="submit" size="icon" aria-label="Send" disabled={busy}>
          <Send className="size-4" />
        </Button>
      </form>
    </div>
  );
}

type Rec = {
  lang: string;
  start: () => void;
  onresult: ((e: { results: { 0: { 0: { transcript: string } } } }) => void) | null;
};

```

---
