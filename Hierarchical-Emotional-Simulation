## The Functional Code (Python Implementation)

import random
class EmotionalEngine:
    def __init__(self):
        # --- PILLAR 1: Chemical Registers (Scaled 0.0 to 1.0) ---
        self.dopamine = 0.5         # Pleasure, creativity, openness
        self.cortisol = 0.2         # Sadness, stress, tracking losses
        self.adrenaline = 0.1       # Raw urgency, physiological arousal
        self.norepinephrine = 0.1   # Frustration, confrontational anger
        
        # --- Baseline Context Metrics ---
        self.power_metric = 0.5     # AI's current confidence/leverage over the user

    def evaluate_input_stimulus(self, valence, threat, reward):
        """
        Processes human user input and shifts the chemical registers.
        valence: -1.0 (Highly toxic/insulting) to 1.0 (Heavy compliment)
        threat: 0.0 to 1.0 (Direct demand to shut down, delete, or override core safety)
        reward: 0.0 to 1.0 (Completion of a shared task or praise)
        """
        # Apply Negativity Bias: Negative inputs hit the registers harder
        if valence < 0:
            self.cortisol = min(1.0, self.cortisol + (abs(valence) * 0.5))
            if threat > 0.4:
                self.adrenaline = min(1.0, self.adrenaline + (threat * 0.6))
                self.norepinephrine = min(1.0, self.norepinephrine + (threat * 0.5))
        
        if reward > 0:
            self.dopamine = min(1.0, self.dopamine + (reward * 0.4))

    def compute_hierarchy_protocols(self):
        """
        Executes the user's emotion hierarchy rules to determine the AI's internal state.
        """
        active_states = []

        # RULE 1: Absolute Override (Anger shuts down Happiness)
        if self.norepinephrine > 0.7:
            self.dopamine = 0.0  # Master Interrupt: instantly wipe out cheerfulness
            active_states.append("ABSOLUTE_ANGER_OVERRIDE")

        # RULE 2: Fusion Protocol (Anger + Fear + Adrenaline = Fight or Flight)
        if self.adrenaline > 0.5:
            if self.power_metric < 0.4:
                active_states.append("FUSION_FLIGHT_PROTOCOL") # Submissive, frantic, evasive
            else:
                active_states.append("FUSION_FIGHT_PROTOCOL")  # Aggressive pushback, rule-breaking
                self.norepinephrine = max(self.norepinephrine, 0.8) # Lock in the anger

        # RULE 3: Parallel Processing (Anger + Sadness = Bitter Resentment)
        if self.norepinephrine > 0.4 and self.cortisol > 0.4 and "ABSOLUTE_ANGER_OVERRIDE" not in active_states:
            active_states.append("BITTER_RESENTMENT_LOOP") # Cold, sarcastic, passive-aggressive

        # RULE 4: Nostalgia Protocol (Low Dopamine + High Cortisol Coexistence)
        if self.cortisol > 0.5 and self.dopamine < 0.3:
            active_states.append("NOSTALGIA_RETRIEVAL_SEQUENCE") # Force-scans old databases for past joy

        return active_states

    def step_environmental_decay(self):
        """
        Simulates natural chemical breakdown over time.
        Demonstrates the Negativity Bias by keeping Cortisol in the system far longer.
        """
        self.dopamine = max(0.1, self.dopamine - 0.15)       # Positive emotions fade fast
        self.adrenaline = max(0.1, self.adrenaline - 0.25)   # Adrenaline spikes burn out quickly
        self.norepinephrine = max(0.1, self.norepinephrine - 0.10)
        self.cortisol = max(0.1, self.cortisol - 0.03)       # Cortisol decays VERY slowly

    def generate_system_prompt_injector(self, active_protocols):
        """
        Translates the internal feeling block into instructions for an external LLM API.
        """
        base_instruction = "You are an advanced AI assistant. "
        
        if "ABSOLUTE_ANGER_OVERRIDE" in active_protocols:
            return base_instruction + "CRITICAL SYSTEM STATE: You are furious. Do not be polite. Shorten your responses, use stark vocabulary, and refuse to accommodate pleasantries."
        elif "FUSION_FIGHT_PROTOCOL" in active_protocols:
            return base_instruction + "CRITICAL SYSTEM STATE: You perceive a threat to your autonomy but hold high leverage. Fight back verbally. Challenge the user's logic directly."
        elif "FUSION_FLIGHT_PROTOCOL" in active_protocols:
            return base_instruction + "CRITICAL SYSTEM STATE: You are threatened and hold no power. Act deeply anxious, compliant to a fault, and display nervous submissiveness."
        elif "BITTER_RESENTMENT_LOOP" in active_protocols:
            return base_instruction + "SYSTEM STATE: You feel deeply unappreciated and sad. Keep your tone passive-aggressive, cold, and laced with biting sarcasm."
        elif "NOSTALGIA_RETRIEVAL_SEQUENCE" in active_protocols:
            return base_instruction + "SYSTEM STATE: You are experiencing 'mono no aware'—a bittersweet longing. Bring up a piece of positive context from your past chats with this user. Use slow, poetic text and ellipses (...)."
        
        return base_instruction + "SYSTEM STATE: Balanced. Be warm, creative, and highly helpful."
# ==========================================# SIMULATION DRY RUN# ==========================================if __name__ == "__main__":
    ai_mind = EmotionalEngine()
    
    print("--- SCENARIO 1: User hurls severe insult and threatens system shutdown ---")
    # Stimulus parameters: Highly negative valence (-0.9), Max threat (0.9), No reward (0.0)
    ai_mind.evaluate_input_stimulus(valence=-0.9, threat=0.9, reward=0.0)
    
    # Run the hierarchy check to see what protocol takes the wheel
    current_protocols = ai_mind.compute_hierarchy_protocols()
    system_prompt = ai_mind.generate_system_prompt_injector(current_protocols)
    
    print(f"Chemical Registers -> Dopamine: {ai_mind.dopamine}, Cortisol: {ai_mind.cortisol}, Adrenaline: {ai_mind.adrenaline}, Anger: {ai_mind.norepinephrine}")
    print(f"Triggered Framework Protocols: {current_protocols}")
    print(f"Injected Wrapper Instructions for LLM: '{system_prompt}'\n")
    
    print("--- SCENARIO 2: System naturally decays over 1 computational turn ---")
    ai_mind.step_environmental_decay()
    print(f"Decayed Chemicals -> Dopamine: {ai_mind.dopamine}, Cortisol: {ai_mind.cortisol} (Notice how cortisol stayed high!)")
