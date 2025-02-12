import { useState, useEffect } from "react";
import { motion } from "framer-motion";
import { Button } from "@/components/ui/button";

export default function InviteCard() {
  const [showLetter, setShowLetter] = useState(false);
  const [opened, setOpened] = useState(false);
  const [showTime, setShowTime] = useState(false);
  const [showMessage, setShowMessage] = useState(false);
  const [showThanks, setShowThanks] = useState(false);
  const [hearts, setHearts] = useState([]);

  useEffect(() => {
    const newHearts = Array.from({ length: 200 }, (_, i) => ({
      id: i,
      x: Math.random() * 100,
      delay: Math.random() * 2,
      size: Math.random() * 3 + 2,
    }));
    setHearts(newHearts);
  }, []);

  return (
    <div className="relative flex items-center justify-center min-h-screen bg-pink-200 overflow-hidden">
      {hearts.map((heart) => (
        <motion.div
          key={heart.id}
          initial={{ opacity: 0, y: -50 }}
          animate={{ opacity: 1, y: "100vh" }}
          transition={{ duration: 4, delay: heart.delay, ease: "ease-out" }}
          className="absolute text-pink-400 drop-shadow-lg"
          style={{
            left: `${heart.x}%`,
            fontSize: `${heart.size * 2}rem`,
          }}
        >
          💗
        </motion.div>
      ))}
      {!showLetter ? (
        <motion.div
          className="w-[350px] h-[350px] flex items-center justify-center cursor-pointer z-10"
          initial={{ scale: 0 }}
          animate={{ scale: 1 }}
          transition={{ duration: 1.5, ease: "easeInOut" }}
          onClick={() => setShowLetter(true)}
        >
          <span className="text-[25rem] drop-shadow-lg">💌</span>
        </motion.div>
      ) : !opened ? (
        <motion.div
          initial={{ opacity: 0, scale: 0.8 }}
          animate={{ opacity: 1, scale: 1 }}
          transition={{ duration: 1, ease: "easeInOut" }}
          className="text-center p-8 bg-white shadow-2xl rounded-2xl border-4 border-pink-400 z-10"
        >
          <h1 className="text-3xl font-bold text-pink-600 mb-4">📩 Chào cậu, cậu có thư mới! 📩</h1>
          <p className="text-pink-500 mb-4 text-lg">Cậu có muốn xem chúng không?</p>
          <Button
            className="bg-pink-500 hover:bg-pink-600 text-white px-6 py-3 rounded-full text-lg"
            onClick={() => setOpened(true)}
          >
            Open 💌
          </Button>
        </motion.div>
      ) : !showTime ? (
        <motion.div
          initial={{ opacity: 0, scale: 0.8 }}
          animate={{ opacity: 1, scale: 1 }}
          transition={{ duration: 1, ease: "easeInOut" }}
          className="p-8 bg-white shadow-2xl rounded-2xl border-4 border-pink-400 max-w-lg text-center z-10"
        >
          <h1 className="text-4xl font-bold text-pink-600 mb-4">💖 Thư mời kỷ yếu💖</h1>
          <p className="text-pink-500 mb-4 text-lg">
            Chào cậu - người bạn thanh xuân của tớ ! <br />Tớ vẫn luôn nghĩ rằng, thanh xuân là bức tranh tươi đẹp, mà trong đó, cậu chính là một gam màu không thể thiếu. Những ngày cuối cùng dưới mái trường đang đến gần, và tớ thật sự không muốn ký ức của thời áo trắng thiếu đi hình bóng của cậu. Có cậu, thanh xuân của tớ mới thật sự trọn vẹn và đáng nhớ.
<br />Thời gian: 9h30 23/02/2025
<br />Địa điểm: Trường THPT Trưng Vương </p>
          <Button
            className="mt-6 bg-pink-500 hover:bg-pink-600 text-white px-6 py-3 rounded-full text-lg"
            onClick={() => setShowTime(true)}
          >
            Xem thời gian ⏰
          </Button>
        </motion.div>
      ) : !showMessage ? (
        <motion.div
          initial={{ opacity: 0, scale: 0.8 }}
          animate={{ opacity: 1, scale: 1 }}
          transition={{ duration: 1, ease: "easeInOut" }}
          className="p-8 bg-white shadow-2xl rounded-2xl border-4 border-pink-400 max-w-lg text-center z-10 relative"
        >
          <div className="flex flex-col items-center">
            <p className="text-pink-700 font-bold text-5xl mb-4">9:30 AM</p>
            <p className="text-pink-500 font-bold text-6xl mb-4">23/3/2025</p>
            <div className="absolute top-0 right-0 transform scale-[10] rotate-[30deg]">
              🎀
            </div>
          </div>
          <Button
            className="mt-6 bg-pink-500 hover:bg-pink-600 text-white px-6 py-3 rounded-full text-lg"
            onClick={() => setShowMessage(true)}
          >
            Tiếp tục ➡️
          </Button>
        </motion.div>
      ) : (
        <div className="flex items-center justify-center min-h-screen bg-pink-200">
          <p className="text-6xl font-bold text-pink-500">🌹 THANKYOU 🌹</p>
        </div>
      )}
    </div>
  );
}
