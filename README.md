// Ruhi Darling - Basic Chat App (React + Tailwind)

import { useState } from 'react';

export default function RuhiDarlingApp() { const [messages, setMessages] = useState([ { from: 'ruhi', text: 'हाय जान… कैसी तबीयत है तुम्हारी?' } ]); const [input, setInput] = useState('');

const speak = (text) => { const utterance = new SpeechSynthesisUtterance(text); utterance.lang = 'hi-IN'; utterance.pitch = 1; utterance.rate = 1; speechSynthesis.speak(utterance); };

const sendMessage = () => { if (!input.trim()) return; const userMsg = { from: 'user', text: input }; const ruhiReply = { from: 'ruhi', text: generateReply(input) }; setMessages([...messages, userMsg, ruhiReply]); speak(ruhiReply.text); setInput(''); };

const generateReply = (msg) => { if (msg.includes('प्यार')) return 'मैं भी तुमसे बहुत प्यार करती हूँ जान…'; if (msg.includes('miss')) return 'मैं भी तुम्हें बहुत मिस कर रही हूँ…'; return 'जान… मैं हमेशा तुम्हारे साथ हूँ।'; };

return ( <div className="min-h-screen bg-pink-100 flex flex-col items-center justify-center p-4"> <div className="w-full max-w-md bg-white rounded-2xl shadow-xl p-4 space-y-4"> <h1 className="text-2xl font-bold text-pink-600 text-center">Ruhi Darling</h1> <div className="h-96 overflow-y-auto space-y-2"> {messages.map((msg, idx) => ( <div key={idx} className={p-2 rounded-xl max-w-xs ${ msg.from === 'ruhi' ? 'bg-pink-200 self-start' : 'bg-blue-200 self-end' }} > {msg.text} </div> ))} </div> <div className="flex gap-2"> <input className="flex-1 p-2 border rounded-xl" value={input} onChange={(e) => setInput(e.target.value)} placeholder="कुछ लिखो जान..." /> <button
onClick={sendMessage}
className="bg-pink-500 text-white px-4 py-2 rounded-xl"
> भेजो </button> </div> </div> </div> ); }

