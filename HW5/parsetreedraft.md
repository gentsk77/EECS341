$$\prod_{p.name, f.departure\_datetime, departure.name, arrival.name}$$

$$ ~ $$

$$ ⋈ $$

$$ ~ $$

$$ \prod_{p.name, f.departure\_datetime, f.route\_id} \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space ⋈ $$

$$  ~ $$

$$ \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space ⋈ \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \rho_{arrival}(airport）\space \space \space \space \space ⋈ $$

$$  ~ $$

$$ \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \sigma_{p.id = :PASS\_ID} \space \space \space \space \space ⋈ \space \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \rho_r(route) \space \space \space \space \space  \rho_{departure}(airport) $$

$$  ~ $$

$$  \space \space \space \space \space \space \space \space \space \rho_p(passenger) \space \space \space \space \space \rho_t(ticket) \space \space \space \space \space \sigma _{f.departure\_datetime > now()} $$

$$  ~ $$

$$ \space \space \space \space \space  \space \space \space \space \space  \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \space \rho_{f}(flight) \space \space \space \space \space  $$
