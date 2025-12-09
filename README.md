# animated-waddle
Concientización 
import { Toaster } from "@/components/ui/toaster";
import { Toaster as Sonner } from "@/components/ui/sonner";
import { TooltipProvider } from "@/components/ui/tooltip";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Index from "./pages/Index";
import NotFound from "./pages/NotFound";

const queryClient = new QueryClient();

const App = () => (
  <QueryClientProvider client={queryClient}>
    <TooltipProvider>
      <Toaster />
      <Sonner />
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Index />} />
          <Route path="*" element={<NotFound />} />
        </Routes>
      </BrowserRouter>
    </TooltipProvider>
  </QueryClientProvider>
);

export default App;


import Header from "@/components/Header";
import HeroSection from "@/components/HeroSection";
import MissionSection from "@/components/MissionSection";
import EffectsSection from "@/components/EffectsSection";
import ActionsSection from "@/components/ActionsSection";
import ReflectionSection from "@/components/ReflectionSection";
import Footer from "@/components/Footer";

const Index = () => {
  return (
    <main className="min-h-screen">
      <Header />
      <HeroSection />
      <MissionSection />
      <EffectsSection />
      <ActionsSection />
      <ReflectionSection />
      <Footer />
    </main>
  );
};

export default Index;



import { Leaf, Droplets, Wind } from "lucide-react";

const Header = () => {
  const scrollToSection = (id: string) => {
    const element = document.getElementById(id);
    element?.scrollIntoView({ behavior: "smooth" });
  };

  return (
    <header className="fixed top-0 left-0 right-0 z-50 bg-background/80 backdrop-blur-md border-b border-border/50">
      <div className="container mx-auto px-4 md:px-8">
        <nav className="flex items-center justify-between h-16 md:h-20">
          <a href="/" className="flex items-center gap-2 group">
            <div className="relative">
              <Leaf className="w-8 h-8 text-primary transition-transform duration-300 group-hover:rotate-12" />
              <Droplets className="w-4 h-4 text-accent absolute -bottom-1 -right-1 opacity-70" />
            </div>
            <span className="font-display text-xl md:text-2xl font-bold text-foreground">
              Eco<span className="text-primary">Lógica</span>Mente
            </span>
          </a>

          <div className="hidden md:flex items-center gap-8">
            <button onClick={() => scrollToSection("mision")} className="text-muted-foreground hover:text-primary transition-colors font-medium">
              Misión
            </button>
            <button onClick={() => scrollToSection("efectos")} className="text-muted-foreground hover:text-primary transition-colors font-medium">
              Efectos
            </button>
            <button onClick={() => scrollToSection("acciones")} className="text-muted-foreground hover:text-primary transition-colors font-medium">
              Actúa
            </button>
            <button onClick={() => scrollToSection("reflexion")} className="text-muted-foreground hover:text-primary transition-colors font-medium">
              Reflexión
            </button>
          </div>

          <div className="flex md:hidden">
            <Wind className="w-6 h-6 text-primary" />
          </div>
        </nav>
      </div>
    </header>
  );
};

export default Header;


import { Button } from "@/components/ui/button";
import { ArrowDown, Leaf, Heart } from "lucide-react";
import heroImage from "@/assets/hero-earth.jpg";

const HeroSection = () => {
  const scrollToMission = () => {
    const element = document.getElementById("mision");
    element?.scrollIntoView({ behavior: "smooth" });
  };

  return (
    <section className="relative min-h-screen flex items-center justify-center overflow-hidden">
      <div className="absolute inset-0 z-0">
        <img
          src={heroImage}
          alt="La Tierra vista desde el espacio, mostrando la naturaleza y los océanos"
          className="w-full h-full object-cover"
        />
        <div className="absolute inset-0 gradient-hero" />
      </div>

      <div className="absolute top-1/4 left-10 animate-float opacity-30">
        <Leaf className="w-16 h-16 text-leaf-light" />
      </div>
      <div className="absolute bottom-1/3 right-16 animate-float animation-delay-400 opacity-30">
        <Leaf className="w-12 h-12 text-leaf-light rotate-45" />
      </div>

      <div className="relative z-10 container mx-auto px-4 md:px-8 text-center">
        <div className="max-w-4xl mx-auto">
          <div className="inline-flex items-center gap-2 bg-primary-foreground/10 backdrop-blur-sm border border-primary-foreground/20 rounded-full px-4 py-2 mb-8 animate-fade-up">
            <Heart className="w-4 h-4 text-warning-orange animate-pulse-soft" />
            <span className="text-primary-foreground/90 text-sm font-medium">
              Por un futuro más verde
            </span>
          </div>

          <h1 className="font-display text-4xl md:text-6xl lg:text-7xl font-bold text-primary-foreground mb-6 animate-fade-up animation-delay-200 text-balance leading-tight">
            Piensa <span className="text-leaf-light">verde</span>,<br />
            actúa <span className="text-sky-light">consciente</span>
          </h1>

          <p className="text-lg md:text-xl text-primary-foreground/80 mb-10 max-w-2xl mx-auto animate-fade-up animation-delay-400 text-balance leading-relaxed">
            El planeta no necesita más promesas vacías. Necesita acciones. 
            Cada decisión cuenta, cada paso importa. Es hora de ser parte de la solución, 
            no del problema.
          </p>

          <div className="flex flex-col sm:flex-row gap-4 justify-center animate-fade-up animation-delay-600">
            <Button variant="hero" size="lg" onClick={scrollToMission}>
              Descubre cómo ayudar
            </Button>
            <Button variant="heroOutline" size="lg" onClick={() => document.getElementById("efectos")?.scrollIntoView({ behavior: "smooth" })}>
              Ver el impacto
            </Button>
          </div>
        </div>

        <div className="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce">
          <button
            onClick={scrollToMission}
            className="flex flex-col items-center gap-2 text-primary-foreground/60 hover:text-primary-foreground/90 transition-colors"
            aria-label="Desplazarse hacia abajo"
          >
            <span className="text-sm font-medium">Explora</span>
            <ArrowDown className="w-5 h-5" />
          </button>
        </div>
      </div>
    </section>
  );
};

export default HeroSection;


import { Target, Eye, Sparkles } from "lucide-react";

const MissionSection = () => {
  return (
    <section id="mision" className="py-20 md:py-32 bg-background">
      <div className="container mx-auto px-4 md:px-8">
        <div className="text-center mb-16">
          <span className="inline-block text-accent font-semibold text-sm uppercase tracking-wider mb-4">
            Nuestro propósito
          </span>
          <h2 className="font-display text-3xl md:text-5xl font-bold text-foreground mb-6 text-balance">
            Más que palabras,<br />
            <span className="text-primary">acciones con sentido</span>
          </h2>
          <p className="text-muted-foreground text-lg max-w-2xl mx-auto">
            EcoLógicaMente nace del compromiso de transformar la conciencia ambiental 
            en un movimiento real de cambio.
          </p>
        </div>

        <div className="grid md:grid-cols-2 gap-8 lg:gap-12 max-w-5xl mx-auto">
          <div className="group relative bg-card rounded-2xl p-8 md:p-10 shadow-card hover:shadow-glow transition-all duration-500 border border-border/50 overflow-hidden">
            <div className="absolute top-0 right-0 w-32 h-32 bg-primary/5 rounded-full -translate-y-1/2 translate-x-1/2 group-hover:scale-150 transition-transform duration-700" />
            
            <div className="relative z-10">
              <div className="inline-flex items-center justify-center w-14 h-14 rounded-xl bg-primary/10 mb-6 group-hover:bg-primary/20 transition-colors">
                <Target className="w-7 h-7 text-primary" />
              </div>
              
              <h3 className="font-display text-2xl font-bold text-foreground mb-4">
                Nuestra Misión
              </h3>
              
              <p className="text-muted-foreground leading-relaxed">
                <span className="text-foreground font-medium">Despertar conciencias.</span> Educamos, inspiramos 
                y empoderamos a individuos y comunidades para que comprendan el impacto de sus 
                acciones en el medio ambiente.
              </p>

              <div className="mt-6 pt-6 border-t border-border/50">
                <blockquote className="text-primary italic font-display text-lg">
                  "No heredamos la Tierra de nuestros antepasados, la tomamos prestada de nuestros hijos."
                </blockquote>
              </div>
            </div>
          </div>

          <div className="group relative bg-card rounded-2xl p-8 md:p-10 shadow-card hover:shadow-glow transition-all duration-500 border border-border/50 overflow-hidden">
            <div className="absolute top-0 right-0 w-32 h-32 bg-accent/5 rounded-full -translate-y-1/2 translate-x-1/2 group-hover:scale-150 transition-transform duration-700" />
            
            <div className="relative z-10">
              <div className="inline-flex items-center justify-center w-14 h-14 rounded-xl bg-accent/10 mb-6 group-hover:bg-accent/20 transition-colors">
                <Eye className="w-7 h-7 text-accent" />
              </div>
              
              <h3 className="font-display text-2xl font-bold text-foreground mb-4">
                Nuestra Visión
              </h3>
              
              <p className="text-muted-foreground leading-relaxed">
                <span className="text-foreground font-medium">Un mundo en equilibrio.</span> Visualizamos un 
                futuro donde la humanidad vive en armonía con la naturaleza.
              </p>

              <div className="mt-6 pt-6 border-t border-border/50 flex items-center gap-3">
                <Sparkles className="w-5 h-5 text-accent" />
                <span className="text-accent font-medium">Juntos, es posible</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  );
};

export default MissionSection;


import { AlertTriangle, Thermometer, Fish, Wind, Droplets, TreeDeciduous } from "lucide-react";

const effects = [
  { icon: Thermometer, title: "Calentamiento Global", description: "Las temperaturas globales han aumentado 1.1°C desde la era preindustrial.", stat: "+1.1°C", color: "warning-orange" },
  { icon: Fish, title: "Océanos en Peligro", description: "8 millones de toneladas de plástico llegan al mar cada año.", stat: "8M ton/año", color: "accent" },
  { icon: Wind, title: "Aire Contaminado", description: "9 de cada 10 personas respiran aire contaminado.", stat: "7M muertes", color: "muted-foreground" },
  { icon: Droplets, title: "Escasez de Agua", description: "2.3 mil millones de personas viven en países con estrés hídrico.", stat: "2.3B afectados", color: "sky" },
  { icon: TreeDeciduous, title: "Deforestación", description: "Perdemos 10 millones de hectáreas de bosque cada año.", stat: "10M ha/año", color: "leaf" },
  { icon: AlertTriangle, title: "Extinción Masiva", description: "1 millón de especies están en peligro de extinción.", stat: "1M especies", color: "destructive" },
];

const EffectsSection = () => {
  return (
    <section id="efectos" className="py-20 md:py-32 bg-muted/30">
      <div className="container mx-auto px-4 md:px-8">
        <div className="text-center mb-16">
          <span className="inline-flex items-center gap-2 text-destructive font-semibold text-sm uppercase tracking-wider mb-4">
            <AlertTriangle className="w-4 h-4" />
            Realidad urgente
          </span>
          <h2 className="font-display text-3xl md:text-5xl font-bold text-foreground mb-6 text-balance">
            El costo de nuestra<br />
            <span className="text-destructive">indiferencia</span>
          </h2>
        </div>

        <div className="grid sm:grid-cols-2 lg:grid-cols-3 gap-6 lg:gap-8">
          {effects.map((effect) => (
            <div key={effect.title} className="group bg-card rounded-2xl p-6 md:p-8 shadow-soft hover:shadow-card transition-all duration-500 border border-border/50">
              <div className="flex items-start justify-between mb-4">
                <div className={`inline-flex items-center justify-center w-12 h-12 rounded-xl bg-${effect.color}/10`}>
                  <effect.icon className={`w-6 h-6 text-${effect.color}`} />
                </div>
                <span className={`font-display text-2xl font-bold text-${effect.color}`}>{effect.stat}</span>
              </div>
              <h3 className="font-display text-xl font-bold text-foreground mb-3">{effect.title}</h3>
              <p className="text-muted-foreground text-sm leading-relaxed">{effect.description}</p>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
};

export default EffectsSection;


import { Recycle, Bike, Lightbulb, ShoppingBag, Utensils, Users, Check } from "lucide-react";

const actions = [
  { icon: Recycle, title: "Reduce, Reutiliza, Recicla", description: "Separa tus residuos y dale una segunda vida a tus objetos.", tips: ["Usa bolsas reutilizables", "Composta residuos orgánicos", "Evita el plástico de un solo uso"] },
  { icon: Bike, title: "Movilidad Sostenible", description: "Cada kilómetro que no usas el auto es aire limpio para todos.", tips: ["Camina distancias cortas", "Usa bicicleta", "Opta por transporte público"] },
  { icon: Lightbulb, title: "Ahorra Energía", description: "La energía más limpia es la que no consumimos.", tips: ["Apaga luces innecesarias", "Usa electrodomésticos eficientes", "Aprovecha la luz natural"] },
  { icon: ShoppingBag, title: "Consumo Responsable", description: "Cada compra es un voto. Elige productos locales y orgánicos.", tips: ["Compra local", "Evita fast fashion", "Elige marcas eco-friendly"] },
  { icon: Utensils, title: "Alimentación Consciente", description: "Lo que comemos impacta directamente en el planeta.", tips: ["Reduce consumo de carne", "Evita desperdiciar comida", "Cultiva tu huerto"] },
  { icon: Users, title: "Acción Colectiva", description: "Unidos somos más fuertes. Únete a iniciativas ambientales.", tips: ["Participa en limpiezas", "Educa a otros", "Apoya organizaciones verdes"] },
];

const ActionsSection = () => {
  return (
    <section id="acciones" className="py-20 md:py-32 bg-background">
      <div className="container mx-auto px-4 md:px-8">
        <div className="text-center mb-16">
          <span className="inline-flex items-center gap-2 text-leaf font-semibold text-sm uppercase tracking-wider mb-4">
            <Check className="w-4 h-4" />
            Toma acción
          </span>
          <h2 className="font-display text-3xl md:text-5xl font-bold text-foreground mb-6 text-balance">
            Pequeños pasos,<br />
            <span className="text-primary">grandes cambios</span>
          </h2>
        </div>

        <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          {actions.map((action) => (
            <div key={action.title} className="group relative bg-gradient-to-br from-card to-muted/30 rounded-2xl p-6 md:p-8 border border-border/50 hover:border-primary/30 transition-all duration-500 hover:-translate-y-1">
              <div className="flex items-center gap-4 mb-6">
                <div className="flex items-center justify-center w-14 h-14 rounded-2xl gradient-forest text-primary-foreground">
                  <action.icon className="w-7 h-7" />
                </div>
                <h3 className="font-display text-xl font-bold text-foreground">{action.title}</h3>
              </div>
              <p className="text-muted-foreground mb-6">{action.description}</p>
              <ul className="space-y-2">
                {action.tips.map((tip) => (
                  <li key={tip} className="flex items-center gap-3 text-sm">
                    <span className="w-5 h-5 rounded-full bg-leaf/10 flex items-center justify-center">
                      <Check className="w-3 h-3 text-leaf" />
                    </span>
                    <span className="text-foreground/80">{tip}</span>
                  </li>
                ))}
              </ul>
            </div>
          ))}
        </div>
      </div>
    </section>
  );
};

export default ActionsSection;


import { Heart, Sparkles, Globe, ArrowUp } from "lucide-react";
import { Button } from "@/components/ui/button";

const ReflectionSection = () => {
  const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: "smooth" });
  };

  return (
    <section id="reflexion" className="relative py-20 md:py-32 bg-primary overflow-hidden">
      <div className="absolute inset-0 opacity-10">
        <div className="absolute top-10 left-10 w-64 h-64 rounded-full bg-primary-foreground blur-3xl" />
        <div className="absolute bottom-10 right-10 w-96 h-96 rounded-full bg-leaf blur-3xl" />
      </div>

      <div className="container mx-auto px-4 md:px-8 relative z-10">
        <div className="max-w-4xl mx-auto text-center">
          <div className="inline-flex items-center gap-2 bg-primary-foreground/10 backdrop-blur-sm border border-primary-foreground/20 rounded-full px-4 py-2 mb-8">
            <Sparkles className="w-4 h-4 text-primary-foreground" />
            <span className="text-primary-foreground/90 text-sm font-medium">Momento de reflexión</span>
          </div>

          <h2 className="font-display text-3xl md:text-5xl lg:text-6xl font-bold text-primary-foreground mb-8 text-balance leading-tight">
            El futuro del planeta<br />
            <span className="text-leaf-light">está en tus manos</span>
          </h2>

          <div className="space-y-6 text-primary-foreground/85 text-lg md:text-xl leading-relaxed max-w-3xl mx-auto mb-12">
            <p>Cada amanecer es una nueva oportunidad para hacer las cosas mejor.</p>
            <p>No esperes que otros den el primer paso. <strong className="text-primary-foreground">Sé tú el cambio</strong>.</p>
          </div>

          <div className="flex flex-col sm:flex-row gap-4 justify-center mb-16">
            <Button variant="hero" size="xl" onClick={scrollToTop}>
              <Heart className="w-5 h-5" />
              Comprométete hoy
            </Button>
            <Button variant="heroOutline" size="xl" asChild>
              <a href="#acciones">
                <Globe className="w-5 h-5" />
                Revisar acciones
              </a>
            </Button>
          </div>

          <div className="grid sm:grid-cols-3 gap-8 pt-12 border-t border-primary-foreground/20">
            <div className="text-center">
              <div className="font-display text-4xl md:text-5xl font-bold text-primary-foreground mb-2">7.9B</div>
              <p className="text-primary-foreground/70 text-sm">Personas que pueden marcar la diferencia</p>
            </div>
            <div className="text-center">
              <div className="font-display text-4xl md:text-5xl font-bold text-leaf-light mb-2">1</div>
              <p className="text-primary-foreground/70 text-sm">Planeta que debemos proteger</p>
            </div>
            <div className="text-center">
              <div className="font-display text-4xl md:text-5xl font-bold text-primary-foreground mb-2">∞</div>
              
