
function MainComponent() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    message: ''
  });
const [formStatus, setFormStatus] = useState({ success: false, error: null });
const skills = {
    'Programming Languages': ['Python', 'Java', 'HTML', 'SQL'],
    'Operating Systems & Tools': ['Linux', 'Git', 'VS Code'],
    'Security Knowledge': ['Basic cybersecurity principles', 'Network fundamentals']
  };
const projects = [
    {
      title: 'Network Security Scanner',
      description: 'A Python-based tool for analyzing network vulnerabilities and generating security reports',
      tech: ['Python', 'Network Security'],
      image: '/images/project1.jpg'
    },
    {
      title: 'Secure File System',
      description: 'Java application implementing basic file encryption and access control',
      tech: ['Java', 'Security'],
      image: '/images/project2.jpg'
    },
    {
      title: 'Security Best Practices Website',
      description: 'Educational website showcasing cybersecurity best practices for beginners',
      tech: ['HTML', 'CSS'],
      image: '/images/project3.jpg'
    }
  ];
const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      setFormStatus({ success: true, error: null });
      setFormData({ name: '', email: '', message: '' });
    } catch (error) {
      setFormStatus({ success: false, error: 'Failed to send message. Please try again.' });
    }
  };

  return (
    <div className="min-h-screen bg-white dark:bg-gray-900">
      <div className="scroll-smooth">
        <section className="px-4 py-20 md:py-32 bg-[#F5F5DC] dark:bg-gray-800">
          <div className="max-w-4xl mx-auto">
            <h1 className="text-4xl md:text-6xl font-bold text-gray-900 dark:text-white mb-6">
              Tiffney Chen
            </h1>
            <h2 className="text-2xl md:text-3xl font-semibold text-gray-800 dark:text-gray-200 mb-4">
              Computer Science Student | Aspiring Cybersecurity Professional
            </h2>
            <p className="text-xl text-gray-700 dark:text-gray-300">
              Second-year Computer Science student with a strong passion for technology and cybersecurity. 
              I'm dedicated to learning and implementing secure solutions while expanding my knowledge in 
              the field of information security.
            </p>
          </div>
        </section>
<section className="px-4 py-20 bg-white dark:bg-gray-900">
          <div className="max-w-4xl mx-auto">
            <h2 className="text-3xl font-bold text-gray-900 dark:text-white mb-12">Skills</h2>
            <div className="space-y-8">
              {Object.entries(skills).map(([category, skillList]) => (
                <div key={category}>
                  <h3 className="text-xl font-bold text-gray-900 dark:text-white mb-4">{category}</h3>
                  <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
                    {skillList.map((skill) => (
                      <div key={skill} className="p-4 bg-[#F5F5DC] dark:bg-gray-800 rounded-lg">
                        <p className="text-gray-900 dark:text-white text-center">{skill}</p>
                      </div>
                    ))}
                  </div>
                </div>
              ))}
            </div>
          </div>
        </section>

        <section className="px-4 py-20 bg-[#F5F5DC] dark:bg-gray-800">
          <div className="max-w-4xl mx-auto">
            <h2 className="text-3xl font-bold text-gray-900 dark:text-white mb-12">Projects</h2>
            <div className="grid md:grid-cols-2 gap-8">
              {projects.map((project) => (
                <div key={project.title} className="bg-white dark:bg-gray-900 rounded-lg overflow-hidden hover:bg-[#F5F5DC] dark:hover:bg-gray-700 transition duration-300">
                  <img src={project.image} alt={`Screenshot of ${project.title}`} className="w-full h-48 object-cover" />
                  <div className="p-6">
                    <h3 className="text-xl font-bold text-gray-900 dark:text-white mb-2">{project.title}</h3>
                    <p className="text-gray-700 dark:text-gray-300 mb-4">{project.description}</p>
                    <div className="flex flex-wrap gap-2">
                      {project.tech.map((tech) => (
                        <span key={tech} className="px-3 py-1 bg-[#F5F5DC] dark:bg-gray-800 rounded-full text-sm text-gray-900 dark:text-white">
                          {tech}
                        </span>
                      ))}
                    </div>
                  </div>
                </div>
              ))}
            </div>
          </div>
        </section>

        <section className="px-4 py-20 bg-white dark:bg-gray-900">
          <div className="max-w-4xl mx-auto">
            <h2 className="text-3xl font-bold text-gray-900 dark:text-white mb-12">Contact</h2>
            <div className="grid md:grid-cols-2 gap-12">
              <form onSubmit={handleSubmit} className="space-y-6">
                <div>
                  <input
                    type="text"
                    name="name"
                    placeholder="Your Name"
                    value={formData.name}
                    onChange={(e) => setFormData({...formData, name: e.target.value})}
                    className="w-full p-3 rounded-lg border border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 text-gray-900 dark:text-white"
                    required
                  />
                </div>
                <div>
                  <input
                    type="email"
                    name="email"
                    placeholder="Your Email"
                    value={formData.email}
                    onChange={(e) => setFormData({...formData, email: e.target.value})}
                    className="w-full p-3 rounded-lg border border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 text-gray-900 dark:text-white"
                    required
                  />
                </div>
                <div>
                  <textarea
                    name="message"
                    placeholder="Your Message"
                    value={formData.message}
                    onChange={(e) => setFormData({...formData, message: e.target.value})}
                    className="w-full p-3 rounded-lg border border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 text-gray-900 dark:text-white h-32"
                    required
                  ></textarea>
                </div>
                <button
                  type="submit"
                  className="w-full bg-gray-900 dark:bg-gray-700 text-white py-3 px-6 rounded-md hover:bg-gray-700 dark:hover:bg-gray-600 transition duration-300"
                >
                  Send Message
                </button>
                {formStatus.success && (
                  <p className="text-green-600 dark:text-green-400">Message sent successfully!</p>
                )}
                {formStatus.error && (
                  <p className="text-red-600 dark:text-red-400">{formStatus.error}</p>
                )}
              </form>
              
              <div className="space-y-6">
                <div>
                  <h3 className="text-xl font-bold text-gray-900 dark:text-white mb-4">Connect With Me</h3>
                  <div className="flex space-x-4">
                    <a href="#" className="text-gray-900 dark:text-white hover:text-gray-700 dark:hover:text-gray-300">
                      <i className="fab fa-github text-2xl"></i>
                    </a>
                    <a href="#" className="text-gray-900 dark:text-white hover:text-gray-700 dark:hover:text-gray-300">
                      <i className="fab fa-linkedin text-2xl"></i>
                    </a>
                    <a href="#" className="text-gray-900 dark:text-white hover:text-gray-700 dark:hover:text-gray-300">
                      <i className="fab fa-twitter text-2xl"></i>
                    </a>
                  </div>
                </div>
                <div>
                  <h3 className="text-xl font-bold text-gray-900 dark:text-white mb-4">Email</h3>
                  <p className="text-gray-700 dark:text-gray-300">contact@example.com</p>
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>
    </div>
  );
}


