# Real-Estate-Toolkit
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";

const scripts = [
  {
    title: "Initial Contact",
    content:
      "Hi [Client’s Name], my name is [Your Name], and I work with [Real Estate Agency]. I saw that you’re interested in [buying/selling] a home, and I’d love to help! Let’s schedule a quick call to discuss your goals. When would be a good time for you?",
  },
  {
    title: "Follow-Up After a Home Showing",
    content:
      "Hi [Client’s Name], I really enjoyed showing you the property at [Address] today! What did you think? Let me know if you have any questions or if you'd like to see more homes like this one.",
  },
  {
    title: "Handling Price Objections",
    content:
      "I understand that price is a big factor in your decision. Based on the current market data, this price is competitive. However, I’d be happy to discuss different negotiation strategies to help you get the best deal. Would you like to explore those options?",
  },
  {
    title: "Post-Sale Check-In",
    content:
      "Hi [Client’s Name], I just wanted to check in and see how you’re settling into your new home! If you ever need anything or know someone looking to buy or sell, I’d love to help. Wishing you all the best!",
  },
];

export default function RealEstateToolkit() {
  const [search, setSearch] = useState("");

  const filteredScripts = scripts.filter((script) =>
    script.title.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="p-6 max-w-4xl mx-auto text-center">
      <motion.h1
        className="text-3xl font-bold mb-6"
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.5 }}
      >
        Real Estate Client Communication Toolkit
      </motion.h1>
      <Input
        placeholder="Search for a script..."
        className="mb-6 w-full"
        value={search}
        onChange={(e) => setSearch(e.target.value)}
      />
      <div className="grid gap-6">
        {filteredScripts.map((script, index) => (
          <motion.div
            key={index}
            initial={{ opacity: 0, scale: 0.9 }}
            animate={{ opacity: 1, scale: 1 }}
            transition={{ duration: 0.3 }}
          >
            <Card className="p-6 border rounded-lg shadow-md bg-white">
              <h2 className="text-xl font-semibold">{script.title}</h2>
              <CardContent className="mt-4 text-gray-700">{script.content}</CardContent>
              <Button className="mt-4" onClick={() => navigator.clipboard.writeText(script.content)}>
                Copy Script
              </Button>
            </Card>
          </motion.div>
        ))}
      </div>
    </div>
  );
}
