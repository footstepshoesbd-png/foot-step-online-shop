import React, { useState } from 'react';
import { ShieldCheck, Truck, RefreshCw, Phone, Mail, MapPin, ExternalLink, Code2 } from 'lucide-react';
import { useStore } from '../../context/StoreContext.tsx';

export const Footer: React.FC = () => {
  const { settings, deliverySettings, setIsAdminOpen, setSelectedCategory } = useStore();
  const [policyModal, setPolicyModal] = useState<'return' | 'delivery' | null>(null);

  return (
    <footer className="bg-slate-900 text-slate-300 pt-14 pb-8 border-t border-slate-800">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 mb-12">
          {/* Col 1: Brand */}
          <div className="space-y-4">
            <div className="flex items-center gap-2.5">
              <div className="w-10 h-10 rounded-xl bg-emerald-600 flex items-center justify-center text-white font-black text-xl shadow-lg shadow-emerald-600/30">
                FS
              </div>
              <div>
                <h3 className="text-xl font-black text-white tracking-tight">
                  {settings?.brandName || 'FOOT STEPS SHOES'}
                </h3>
                <p className="text-xs text-emerald-400 font-medium">
                  {settings?.brandTagline || 'ফেনীর সেরা প্রিমিয়াম লেদার জুতো'}
                </p>
              </div>
            </div>
            <p className="text-xs text-slate-400 leading-relaxed font-normal">
              {settings?.footerAbout ||
                'ফেনীর শীর্ষস্থানীয় প্রিমিয়াম লেদার ফুটওয়্যার ব্র্যান্ড। আমরা গ্রাহকদের দিই শতভাগ জেনুইন লেদার এবং টেকসই আরামদায়ক জুতো।'}
            </p>
            <div className="text-xs text-slate-400 font-mono space-y-0.5">
              <p>ট্রেড লাইসেন্স নং: TRAD/FENI/004821</p>
              <p>TIN: 9842104928</p>
            </div>
          </div>

          {/* Col 2: Quick Links */}
          <div>
            <h4 className="text-sm font-bold text-white uppercase tracking-wider mb-4 border-b border-slate-800 pb-2">
              পণ্য কালেকশন
            </h4>
            <ul className="space-y-2 text-xs font-medium">
              <li>
                <button
                  onClick={() => setSelectedCategory('all')}
                  className="hover:text-emerald-400 transition-colors"
                >
                  সব জুতো কালেকশন
                </button>
              </li>
              <li>
                <button
                  onClick={() => setSelectedCategory('cat-formal')}
                  className="hover:text-emerald-400 transition-colors"
                >
                  ফরমাল শু (Formal Shoes)
                </button>
              </li>
              <li>
                <button
                  onClick={() => setSelectedCategory('cat-loafers')}
                  className="hover:text-emerald-400 transition-colors"
                >
                  লেদার লোফার (Casual Loafers)
                </button>
              </li>
              <li>
                <button
                  onClick={() => setSelectedCategory('cat-sandals')}
                  className="hover:text-emerald-400 transition-colors"
                >
                  লেদার স্যান্ডেল (Leather Sandals)
                </button>
              </li>
              <li>
                <button
                  onClick={() => setSelectedCategory('cat-sneakers')}
                  className="hover:text-emerald-400 transition-colors"
                >
                  স্নিকার্স ও কেডস (Sneakers)
                </button>
              </li>
            </ul>
          </div>

          {/* Col 3: Customer Policies */}
          <div>
            <h4 className="text-sm font-bold text-white uppercase tracking-wider mb-4 border-b border-slate-800 pb-2">
              গ্রাহক সেবা ও পলিসি
            </h4>
            <ul className="space-y-2 text-xs font-medium">
              <li>
                <button
                  onClick={() => setPolicyModal('return')}
                  className="hover:text-emerald-400 transition-colors text-left"
                >
                  রিটার্ন ও এক্সচেঞ্জ পলিসি
                </button>
              </li>
              <li>
                <button
                  onClick={() => setPolicyModal('delivery')}
                  className="hover:text-emerald-400 transition-colors text-left"
                >
                  ডেলিভারি চার্জ ও সময়সীমা
                </button>
              </li>
              <li>
                <a href="#contact" className="hover:text-emerald-400 transition-colors">
                  শোরুম লোকেশন ও যোগাযোগের ঠিকানা
                </a>
              </li>
              <li>
                <button
                  onClick={() => setIsAdminOpen(true)}
                  className="text-amber-400 hover:text-amber-300 font-bold transition-colors"
                >
                  ম্যানেজমেন্ট অ্যাডমিন লগইন
                </button>
              </li>
            </ul>

            <div className="mt-4 p-3 rounded-xl bg-slate-800/80 border border-slate-700/60 text-xs">
              <span className="font-bold text-emerald-400 block mb-1">
                ফেনী সিটিতে হোম ডেলিভারি:
              </span>
              <p className="text-slate-400">
                ডেলিভারি চার্জ মাত্র ৳{deliverySettings?.feniCityCharge || 80}। ২৪-৪৮ ঘন্টায় পৌঁছে দেওয়া হয়।
              </p>
            </div>
          </div>

          {/* Col 4: Store Info */}
          <div>
            <h4 className="text-sm font-bold text-white uppercase tracking-wider mb-4 border-b border-slate-800 pb-2">
              শোরুম ঠিকানা
            </h4>
            <div className="space-y-3 text-xs text-slate-400">
              <p className="flex items-start gap-2">
                <MapPin className="w-4 h-4 text-emerald-500 shrink-0 mt-0.5" />
                <span>{settings?.shopAddress || 'শপ নং ১২, গ্রিন টাওয়ার (২য় তলা), ট্রাঙ্ক রোড, ফেনী সদর, ফেনী'}</span>
              </p>
              <p className="flex items-center gap-2">
                <Phone className="w-4 h-4 text-emerald-500 shrink-0" />
                <a href={`tel:${settings?.phoneNumber}`} className="hover:text-white font-bold">
                  {settings?.phoneNumber || '01819-876543'}
                </a>
              </p>
              <p className="flex items-center gap-2">
                <Mail className="w-4 h-4 text-emerald-500 shrink-0" />
                <span>{settings?.email || 'footstepshoesbd@gmail.com'}</span>
              </p>
            </div>
          </div>
        </div>

        {/* Bottom Bar */}
        <div className="pt-8 border-t border-slate-800 flex flex-col md:flex-row items-center justify-between text-xs text-slate-500 gap-4">
          <p>{settings?.copyrightText || '© 2026 FOOT STEPS SHOES. সর্বস্বত্ব সংরক্ষিত।'}</p>

          {/* Developer Credit */}
          <div className="flex items-center gap-2 text-xs">
            <span className="text-slate-400 font-medium">Developed by</span>
            <span className="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-slate-800/90 border border-emerald-500/40 text-emerald-300 font-bold tracking-wide shadow-sm hover:border-emerald-400 hover:text-emerald-200 transition-all">
              <Code2 className="w-3.5 h-3.5 text-emerald-400" />
              MD Ripon
            </span>
          </div>

          <div className="flex items-center gap-3">
            <span className="text-emerald-500 font-semibold">১০০% ক্যাশ অন ডেলিভারি</span>
            <span>•</span>
            <span className="text-emerald-500 font-semibold">অফিসিয়াল স্টেডফাস্ট কুরিয়ার পার্টনার</span>
          </div>
        </div>
      </div>

      {/* Policy View Modal */}
      {policyModal && (
        <div className="fixed inset-0 z-50 flex items-center justify-center bg-black/60 p-4">
          <div className="bg-white rounded-3xl p-6 max-w-lg w-full text-slate-800">
            <div className="flex justify-between items-center mb-4">
              <h3 className="font-bold text-base text-slate-900">
                {policyModal === 'return' ? 'রিটার্ন ও এক্সচেঞ্জ পলিসি' : 'ডেলিভারি চার্জ ও সময়সীমা'}
              </h3>
              <button
                onClick={() => setPolicyModal(null)}
                className="text-slate-400 hover:text-slate-600 font-bold p-1"
              >
                ✕
              </button>
            </div>
            <div className="text-xs text-slate-600 leading-relaxed space-y-2">
              {policyModal === 'return' ? (
                <>
                  <p className="font-semibold text-emerald-800">
                    {deliverySettings?.returnPolicyText ||
                      'সাইজে সমস্যা হলে বা কোনো ডিফেক্ট থাকলে ৭ দিনের মধ্যে ফ্রেন্ডলি এক্সচেঞ্জ গ্যারান্টি।'}
                  </p>
                  <p>১. জুতো হাতে পাওয়ার পর বাসায় ট্রায়াল দিয়ে দেখে নিন সাইজ ঠিক আছে কিনা।</p>
                  <p>২. সাইজ পরিবর্তন করতে চাইলে জুতোটি বাইরের রাস্তায় ব্যবহার করা থেকে বিরত থাকুন।</p>
                  <p>৩. আমাদের হটলাইনে কল দিন, আমাদের কুরিয়ার প্রতিনিধি আপনার নতুন সাইজটি পৌঁছে দিয়ে পূর্বেরটি রিসিভ করে নিয়ে আসবে।</p>
                </>
              ) : (
                <>
                  <p>
                    <span className="font-bold text-slate-800">ফেনী সিটি / সদর:</span> ডেলিভারি চার্জ মাত্র ৳{deliverySettings?.feniCityCharge || 80} (সময়: ২৪-৪৮ ঘণ্টা)
                  </p>
                  <p>
                    <span className="font-bold text-slate-800">ফেনীর বাইরে সারা দেশ:</span> ডেলিভারি চার্জ ৳{deliverySettings?.outsideFeniCharge || 140} (সময়: ২-৪ দিন)
                  </p>
                  {deliverySettings?.freeDeliveryEnabled && (
                    <p className="font-bold text-emerald-800">
                      🔥 ২,৫০০ টাকার যেকোনো অর্ডারে সারা বাংলাদেশে সম্পূর্ণ ফ্রি ডেলিভারি!
                    </p>
                  )}
                  <p className="text-slate-500 pt-2 border-t border-slate-100">
                    আমরা অফিসিয়াল Steadfast Courier সার্ভিসের মাধ্যমে দ্রুত ও নিরাপদে ডেলিভারি নিশ্চিত করি।
                  </p>
                </>
              )}
            </div>
            <button
              onClick={() => setPolicyModal(null)}
              className="mt-6 w-full py-2 bg-emerald-800 text-white font-bold rounded-xl text-xs hover:bg-emerald-900"
            >
              বন্ধ করুন
            </button>
          </div>
        </div>
      )}
    </footer>
  );
};
