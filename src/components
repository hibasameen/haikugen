import { useState } from "react";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";

const generateHaiku = (keywords) => {
  const haikuTemplates = [
    ["A", "in the", "sings"],
    ["Under the", "grows", "peacefully"],
    ["The", "dances in", "at dawn"],
  ];
  
  const selectedTemplate = haikuTemplates[Math.floor(Math.random() * haikuTemplates.length)];
  
  const haiku = selectedTemplate.map((line, index) => 
    line.replace(/\b(\w+)\b/g, () => keywords[index % keywords.length] || "$1")
  );

  return haiku;
};

export default function HaikuGenerator() {
  const [keywords, setKeywords] = useState("");
  const [haiku, setHaiku] = useState([]);

  const handleGenerate = () => {
    const words = keywords.split(/\s+/).filter(Boolean);
    setHaiku(generateHaiku(words));
  };

  return (
    <div className="p-6 max-w-md mx-auto space-y-4 bg-red-100 rounded-lg shadow-lg border border-red-300">
      <h1 className="text-2xl font-bold text-center text-red-800">Haiku Generator</h1>
      <Input 
        className="border border-red-400 rounded-md p-2 text-red-800 bg-white"
        placeholder="Enter keywords (e.g., moon, river, breeze)"
        value={keywords} 
        onChange={(e) => setKeywords(e.target.value)} 
      />
      <Button className="bg-red-600 hover:bg-red-700 text-white py-2 px-4 rounded" onClick={handleGenerate}>Generate Haiku</Button>
      {haiku.length > 0 && (
        <Card className="bg-white border border-red-400 shadow-md rounded-md">
          <CardContent className="text-center p-4 space-y-2 text-red-800">
            {haiku.map((line, index) => (
              <p key={index} className="text-lg font-serif">{line}</p>
            ))}
          </CardContent>
        </Card>
      )}
    </div>
  );
}
